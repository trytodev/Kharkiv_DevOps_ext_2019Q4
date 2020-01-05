# Task 3.1
### Cisco Packet Tracer pt. 2

In this practical task i've builded a complex network using Cisco Packet Tracer software and learned how to restrict traffic and setup VLAN.

### First part
Create a network of a building with 4 floors. Each floor must contain 3 PCs in one workgroup and 5 PCs in second (8 groups total), but clients from the 1st floor and 3rd floor cannot communicate with each other.
After creating a general model and setting up addresses for every router and PC inside the network i've checked a communication between different subnets.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/floor_1_to_3.png)

Currently everyone can "talk" to everyone, but we need to restrict traffic between floors 1 and 3.
For this i've used default functionality - ACL (Access Control List). It can be configured in CLI of the router. In my case was choosen routers 1 and 3. For the 1 i created rule to restrict traffic from all addresses in 192.168.5.x and 192.168.6.x networks. Rule:
```
access-list 13 deny 192.168.5.0 0.0.0.255
access-list 13 deny 192.168.6.0 0.0.0.255
access-list 13 permit any
```
For the Router 3 rule is 
```
access-list 13 deny 192.168.1.0 0.0.0.255
access-list 13 deny 192.168.2.0 0.0.0.255
access-list 13 permit any
```

In both cases two first rows sets the "deny" for all the traffic from a specified network and third row - allows any other traffic to come in and out. After this needed to apply rules. In Router 1 command is:
```
int fa0/0
ip access-group 13 out
int fa1/0
ip access-group 13 out
```
Router 3:
```
int fa0/0
ip access-group 13 out
int fa1/0
ip access-group 13 out
```
First and third rows says "select a port", second and last - "apply rule for current port".
After this all traffic between floor 1 and 3 are restricted.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/deny_1.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/deny_2.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/deny_3.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/deny_4.png)


### Second part

Create a network of 5 buildings with 5 workgroups (6 PCs in each group). All network based on router with one port. Traffic between buildings 1 and 5 must be restricted.

To build network in this case i've used 5 switches to create workgroups, 1 switch to connect them between each other and to connect all this to one router. Cause we restricted with hardware - VLAN is gonna be our saviour.
First - the structure of 5 main switches are identical. Ports fa0/1 - fa3/1 and eth6/1 - eth7/1 are using to connect PCs to Switch, while port fa4/1 is used for connection to "general" switch.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/general_vlan.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/local_switch.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/local_switch_general.png)

VLAN's can be created automatically while assigning it to the port. In my case it looked like
```
int fa4/1 (select port)
switchport mode access (change mode)
switchport access vlan 11 (assign a vlan to port)
```
After this it is possible to setup the rest ports using user inteface or continue with CLI. When all needed ports on a switch configured - move to next one.
When every switch is done, time to work with "general".
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/general_switch.png)

In this case is not enough to setup VLAN, it is also needed to setup "trunk" mode on a port which is connected with router. In this mode traffic from all the VLAN's could be send to the router. For this on port fa9/1 mode was changed from mode "access" to "trunk". On router was created virtual adapters (repeat for each VLAN with change of port, VLAN and address):
`int fa4/0.11` (select port and after dot - add virtual port)
`encapsulation dot1Q 11` (encapsulation of traffic on a specified subinterface)
`ip address 192.168.1.10 255.255.255.0` (assign gateway)
`no shutdown`
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/router.png)

After this all clients could send data between each other.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/vlan_test.png)

But we need to setup a "deny" for builings 1 and 5. For this was created two rules:
```
access-list 13 deny 192.168.1.0 0.0.0.255
access-list 13 permit any
access-list 14 deny 192.168.5.0 0.0.0.255
access-list 14 permit any
```

which was applied for virtual ports:
```
int fa4/0.15
ip access-group 13 out
int fa4/0.11
ip access-group 14 out
```

![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/proof.png)