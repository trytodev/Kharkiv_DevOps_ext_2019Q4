# Report for the task 1.2

### Main objective

The main purpose of the task was to give a practical experience of working with GIT and simulating different situations to understand how to deal with them.

Task starts from setting up GIT on local machine, changing config

![setup](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/setup.png)

and getting a GitHub account and creating new repository.
After this i've cloned repo to my PC

![clone](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/clone.png)

and created general structure of the project

![mkdir](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/mkdir.png)

After creating initial structure and adding first file to the repo goes initial commit, which is not possible without using "git add ." command (this is needed to index file (or multiple files) to make commit)

![commit](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/commit.png)

Then i created new branch "develop" and switched to it

![switch](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/switch.png)

to add new files. Then created new branch, "styles", and added some files to it. After commits and changing branch back to "develop" merge process goes in. On this step was conflict between branches (wich was solved by some "magic"), and then one more merge into "master" branch.

![merge_to_master](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/merge_to_master.png)

Every commit is displayed in "git log"

![log](https://github.com/trytodev/Kharkiv_DevOps_ext_2019Q4/tree/master/m1/task1.2/images/log.png)


##### Results

In result was created file with all steps of using GIT in this task, which was pushed to the repo. This practical task gived me an experience with GIT, it's main commands and practice in resolving conflicts between branches.