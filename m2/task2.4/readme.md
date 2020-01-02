# Task 2.4
### Amazon ECS

In this practical task i've deployed a docker container using Amazon ECS (Elastic Container Service) and ELB (Elastic Load Balancing).
ECS allows to run Docker applications in very simple ways and ELB could control multiple containers from a single place. Tasks in ECS are run on a cluster which is the set of container instances running the Amazon ECS container agent.

After ECS setup AWS launching all needed services.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/setup.png)

Then when service is ready you can check if everything works fine.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/success.png)

When all is done i've removed task and load balancer to avoid getting bills.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/remove.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/remove_2.png)
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/in_progress.png)

After the final message you can make sure that everything is clear and shiny.
![img](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m2/task2.4/img/finish.png)