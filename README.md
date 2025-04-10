# GIT-VCS

- If developer is working on diff features (f1,f2,f3) and he keeps on updating the code from f1 to f3. He doesnt maintain any copy of f1 or f2. When f3 is developed but client doesn't want f3 he instead want f1. So here we cannot get the previous version if we dont have version control system
- If multiple developers are working of different features and they have to merge all the changes in one single software, there will be conflicts in changes implemented/written. So without version control system, we cannot determine who has implemented which part.
- When multiple developers are working on same code, we need to have tracking of code whom have written what. This is done by VCS (Version Control system)

Uses of VCS
-
- Maintain different versions of software
- Tracking of changes in projects
- To have central system where all the code is available which is written by multiple developers for single feature which results in sharing files/code between developers for review,etc

Features of VCS
-
- Backup and restore :- keeps files safe against accidental losses or mistakes
- Collaboration :- Multiple people can work on same project simultaneously
- Branching and merging :- Users can diverge from main base of code, experiment and then bring changes back in line without losing work
- Tracking changes :- We can check specific changes made and developer histroy

Types of VCS
-
**1. Centralized Version Control System**
- Developers work on different systems on codes known as Working Copy which are in their local machines. These copies are put on a central/common server with help of network.
- Files in local are sent to server using the network known as commit operation (**checkin**). Code present on server need to be taken on local machine known as **checkout** process
- Commits and checkouts happen only on server side. That's why it is called Centralized repository/VCS

- If network is not available, developers cannot perform checkin/checkout, operation is failed. Also, if server goes down, whole VCS goes down
- If developers and projects are more, difficult to maintain in one single server
e.g:-  SVN

**2. Distributed Version Control System**
- Every developer maintains own workspace(folder where all files are stored) in local. Here they need to maintain some repositories locally. Here commit, checkout, update operations will be done in local repository. So here no network is required
- But here developers send the code to one remote repository where individuals have their own repositories/copies and in remote repository main copy will be maintained
- In remote repository there will be multiple branches and master branch. Everyone will merge code in sub branches not in master branch. Here commit means files in workspace we send to local repo and reverse is update/checkout
- Once we have remote repositories, push and pull will be done. Push means to send from local repo to remote repo and pull is remote to local. Push and pull happens between repo to repo
- Commit and checkout happens between workspace and local repo

- Here there is no single point of failure like Centralised (server), if server goes down and all. Also commit happens in server level. In distributed, we dont need network/server for checkout as everyone maintain their own repository

e.g:- GIT

GIT Architecture and Workflow
-
- GIT is a software which supports distributed version control systems and is open source
- There are 4 major components/parts of GIT  :- Working directory, Staging/Index area, (Git) local repository, (Github) remote repository  

**1. Working Directory (Workspace)**
- Location where actual project files are present
- Files here are called untracked files
- It is location on developer's local machine

**2. Staging area**
- We cannot commit the files from workspace into local repository (1st stage to 3rd). It should go through staging area
- Staging is virtual layer between workspace and local repository
- By adding files from workspace into staging, we make them tracked files and then commit into local repository
- It is a virtual location present in local machine itself

**3. Local Repository**
- Files from staging are committed to local repository where we call them as committed files 

**4. Remote repository**
- When files committed to local repository, we can push them to remote repository from where others can also access them. This is basically a shared location
- Files here we call as remote files

![image](https://github.com/user-attachments/assets/bd030fd6-8b73-4c45-b301-22ed6332a0ec)

e.g:- Suppose we have files in workspace and we've to send them to staging :- **"add"**
      To commit files in local repo :- **"commit"**
      To push files from local to remote :- **"push"**

- Suppose, if any other developer committed the code in remote which is not present into local, we can pull that code from remote to our local and then we can access them through workspace at the end to modify
- Update, commit, checkout will happen in your workspace, local repository while push and pull happens in remote machines
- If we dont have any local repo and have remote one and want to download or check remote projects, we can just "clone" the remote project into local repository/ or which will create one local repository
- Local repository is created by GIT and available in local machine
- Remote repository is created by us using GITHUB/GITLAB
- Each individual will add their code in various branches in remote repository in GITHUB in which there can be conflicts. After resolving conflicts, final code will be merged into "master" branch


