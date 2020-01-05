# Task 3.1
### Cisco Packet Tracer

In this practical task i've builded a network using Cisco Packet Tracer software and learned it's basic funcionality.

Step 1 - created a small network with 1 Hub and 4 PCs. This metod for device communication is simple and cheap, but ineffective cause all packets inside the network are sended to every client in the network.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/1.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/pdu_1.png)

Step 2 - network expanded, added one more Hub, Server and 2 PCs. Also in this metod of communication all devices must be within the same subnet.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/pdu_2.png)

Step 3 - created a new network with 2 switches and 4 PCs connected to each. Switches connected between each other using Copper Cross-over cable.
When instead of Hub's we started use Switches all of the data sending directly to the client without disturbing other machines around it.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/pdu_3.png)

Step 4 - added Router to the existing network and PCs from 4 to 7 moved to the new subnet (192.168.1.x). Router makes possible to send data among clients in different subnetworks without a need of setup VLAN.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/pdu_4.png)