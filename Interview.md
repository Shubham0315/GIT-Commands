# Interview Questions

1. What is GIT?
- Git is a distributed VCS used to track changes in source code during software development. It allows multiple developers to work on a project together without interrupting each other's work.

2. What is Git repository?
- It is a file like structure storing all project files. It continues to track changes in the files over time

3. Difference between GIT and GITHub
- Git is a VCS local to our machine to track changes in a file over time whereas Github is a cloud based platform  where Git repos from local can be shared and people can use them.
- Git doesnt require network whereas Github does.

4. What is origin in GIT?
- It referes to default name offered to remote repository from which local repository was cloned. It is used as reference to control fetches, pulls and pushes

5. .gitignore file?
- Tells git which files or directories it should ignore when tracking changes in a repository.
- It is useful for excluding temporary files, build artifacts, config files or sensitive data that dont need to be versioned.

6. What is VCS and its types?
- VCS is a central system where all the code written by developers is available and others can take reference from our code or clone for their use.
- **Centralised VCS** :- Developers working on different system might not have copy of files on local system. These copies of files are put on central server with the help of network. Non-availability of network results in failed checkin/checkout. If server goes down, whole VCS goes donw
- **Distributed VCS** :- Every developer has copy of all versions of code on their system. In distributed, commit/checkout happens on local so no network is needed. Dev just need to push code to remote repo where its copy is maintained for other's use. So even server goes down, we'll have our copy on local and we can checkin once server is up

7. Download any remote repo to local
- Command :- **git clone $URL**

![image](https://github.com/user-attachments/assets/06625177-d59e-4a66-bb13-05f2a4547183)
![image](https://github.com/user-attachments/assets/0d82ff0e-8c5d-4b75-b75e-95f3c77add2b)

- Even if there is no local repository available and we want to download remote projects, we can clone it, it creates local repo for us.

8. How to push file from local to GitHub?
- First connect local repo to remote repo :- **git remote add origin $URL**
- Push files from local to remote :- **git push origin master**

![image](https://github.com/user-attachments/assets/3fdd36d2-40e6-47f4-b821-e655324bed21)
![image](https://github.com/user-attachments/assets/f3e097a2-efa2-4936-80e4-e8338851c202)

9. How is bare repo different from standard way of initializing a git repo?
- When we initialize a repo, there are 2 common types of repos :- bare and non-bare(std one)
- a. Non bare repo (Standard initialization)
  - Command :- git init
  - Create .git repo inside project folder which holds all the metadata of repo (commit history, config,etc)
  - We can use this repo when we're working on code directly in that directory where we can make changes, add files, commit, interact with repo locally. Working directory contains our actual files which we can edit, commit, push changes

  ![image](https://github.com/user-attachments/assets/f9952541-c526-49d9-b5a9-f8be79a351c7)
  
- b. Bare repo
  - Command :- git init --bare
  - It doesnt contain working directory with files that you can edit. Instead it only stores git metadata (.git folder) but not with actual project files
  - These are typically used as central repos where other developers push/pull changes
  - There're no editable files in bare repo

- Non bare has working directory with editable actual files whereas bare ones dont, they'e only .git metadata
- Non-bare Used for local development, whereas bare is used for remote repos where changes are pushed/pulled but not directly modified
- In short, a bare repository is meant for storing and managing Git history (for remote use), while a non-bare repository (standard) is for actual development work.

10. How to revert a commit that is already pushed and made public?
- a. Revert a commit :- It creates a new commit that undoes changes introduced by previous commit
  - Steps :- Identify commit hash --> revert commit (git revert $commit_hash) --> push the reverted commit (git push)
- b. Reset previous commit :- If we want to remove the commit history completely , use git reset. Not recommended as it rewrites history
  - Steps :- Identify commit to reset (git log) --> reset that commit (git reset --hard $commit_id) --> force push the changes (git push origin branch --force)

11. Git fetch and Git pull
- **git fetch** :- downloads new commits and updates remote branches without modifying our working directory or local branches. Doesnt integrate remote changes into current work without affecting local branch
  - Command :- **git fetch origin**

  ![image](https://github.com/user-attachments/assets/a8ce741b-aedc-4bbb-a6ea-e0985474dad7)

- **git push** :- does everything fit fetch does and auto merges fetched changes into current local branch. Updates our working directory and commits, bringing local branch up to date with remote branch.
  - Command :- **git pull origin master**
 
  ![image](https://github.com/user-attachments/assets/73e71175-f6ee-4044-8eda-2afbc27c757c)


12. What is git stash?
- 
























