# Task 2.2
### VirtualBox and Vagrant

### Part 1. VirtualBox

Task started from installation of the VirtualBox and installing Ubuntu on the VM.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/install.png)
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/installed.png)

Then i've checked basic functionaity of the VBox - shut down VM, save it's current state, state reset, etc.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/control.png)
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/save_state.png)
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/reset_state.png)

One of the powerfull parts of the VBox is ability to save different states of the VM if it needed.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/snapshots.png)

All information stored on Virtual Hard Drive, which can be moved to any computer so user can resume his work on any PC with compatible hypervisor. Also it is possible to setup "Shared folder" between VM and host machine.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/shared_folder.png)

VM have virtual network adapters, which can work in different modes so different users can have different access to the network. There is a general overview of modes.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/modes.png)

VMs can see be configured not to see one each other or to VM1 see VM2, but VM2 don't see VM1, like showed below.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/connection_no.png)

Or everyone (host machine, all VMs) can see each other.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/connection_yes.png)

One of the very useful features of VirtualBox is ability to control VMs through the command line interface.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/vboxmanage.png)

With command line i can reset VM, power it up or see current configuration.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/cli_reset.png)
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/startvm.png)
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/info.png)

### Part 2. Vagrant

After creating folder for project and launching PowerShell, I've faced some errors with Vagrant and VirtualBox compatibility, which was solved by downgrading version of VBox to 6.0. But this move not only solved previous problems, but also added new ones. This was little harded to fix, but answer was pretty simple - add "vboxmanage.exe" and "powershell" to the PATH variable.
Vagrant it's a tool for automatization control of VMs. By default VM have predifined configuration, so user can simply initialize machine and use "vagrant up" to launch it / power it off.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/halt.png)

Default path to the VM powered by Vagrant is used from current VBox settings, so to setup 2 VMs i've changed it.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/default.png)

After it i added some lines to the initial "Vagrantfile", which are changed name of VMs, it's box, network adapter type, IP address and number of resources for VM. "ping" showed successfull connection between both VMs.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/ping.png)

In the final part of the task i've created a custom Vagrant box out of my VM.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/add_box.png)

For this i installed PHP to the VM. 
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/pre-config.png)

Then placed VM to the box, booted it up and checked PHP version through the SSH.
![img]https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/blob/master/m1/task2.2/images/custom.png)

But before everything worked, i done few things:
- reconfigured network adapter on VM;
- downgraded "openssh-client" on VM due to errors on "openssh-server" installation process;
- modified "openssh" settings.

##### Results
In this practical task i've learned how to use VirtualBox for setting up Virtual Machine, checked basic functionality of the hypervisor, used Vagrant for automatization of VM setup and learned how to resolve software conflicts to make everything work.