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

![image](https://github.com/user-attachments/assets/943a28b6-bbf8-4f00-a1c2-01225f1bd04d)
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
- We're working on our main code in master branch but we want to modify something without interrupting master branch. This is done by "Git Stash"
- It allows to modify files by switching to other branch to work on something else.
- This saves our uncommitted changes so that we can work on something else or switch branches without losing our progress.
  - We can also apply the stashed changes to our working directory and also do a "pop" to remove stash entry adter applying the changes
  - If we want to continue working where we left work **git stash apply** is used to bring back saved changes onto our current working directory

13. Commands to remove files in git
- **git rm file** :- from workspace and staging
- **git rm --cacahed file** :- only from staging
- **rm file** :- from workspace

14. git checkout
- Various uses :- switch between branches and restore files in working directory
- Command to switch branch :- **git checkout -b branch**

- Also used to restore files to the state in a particular commit, branch or tag. Useful when we want to discard changes in working directory for specific files
  - Command :- **git checkout -- file**
- To restore to specific commit :- **git checkout commit_id -- file**

- It is also used to discard unstaged changes in the tracked files in workspace

15. What is git reset?
- Used to remove unwanted changes from staging and to undo commits from repository level
- 3 modes :- hard, soft, mixed --> all explained

16. Explain git branching commands
- **git branch** :- to view available branches
- **git branch $branch** :- to create new branch from master
- **git checkout $branch** :- switch branch
- **git checkout -b $branch** :- to create new branch and switch to it
- **git branch -d $branch** :- to delete branch in local
- **git push origin --delete branch-name** :- Remote branch deletion

17. Explain git merging techniques
- Fast forward merge and 3 way merge

18. How to resolve conflicts in git?
- Explained in md

19. What is git rebase?
- Explained in md

20. Difference between fast forward and 3 way merge
- If from creation of child branch to merging, if no commit happens to master branch then it is "Fast Forward Merge". If we commit the changes parallely in master as well, it is 3 way merge
- Fast forward is linear while 3 way is non linear
- In FF for every commit there is only 1 parent commit. In 3 way there can be mulyiple parent commits.

21. Difference between merge and rebase
- Everytime we can go for merge whether there are conflicts or not. After merging and resolving we can push to remote. In normal merge, history is also preserved
- Rebase can be only used within local. Only you are responsible for your changes and can create multiple branches and rebase them as needed. So advisable not to use rebase for remote repository as multiple developers can be using the master branch. In rebase history is not maintained as feature gets vanished
- Only if you want to follow linear, then go for rebase
- In merge history is preserved, not in rebase
- Merge Can be used for 3 way or FF while rebase only for FF

22. How to find list of files that have been changed in specific commit?
- Command :- **git diff-tree -r $commit_id**
  - -r allows command to list individual files

![image](https://github.com/user-attachments/assets/c7ecad11-5f34-402d-80c8-161ed5a1b233)

23. Difference between git and SVN
- Git is distributed whereas SVN is centralized VCS
- In git clients can clone entire repo on local while in SVN version histroy is stored on server side of repo
- Using git we can do offline commits as well while in SVN only online commits are allowed (using network)
- In git push/pull operations are faster while on SVN they're slower

24. What is a conflict in git?
- Git conflict occurs when git is unable to automatically merge changes between two branches as both branches have modifications to same part of code that cannot be reconciled automatically
- Even if a file is deleted in one branch and edited in other, conflict arises

25. What is subgit?
- It is tool for SVN to git migration
- It can create writable git mirror of local or remote SVN repo and use both SVN and git as long as you like

26. What is staging area or index?
- It is virtual layer between workspace and local where we can add files and make them tracked
- Before completing commits, any change can be formatted and reviewed in intermediate area which is "**STAGING**"

27. What is git is-tree?
- This command is used to display contents of tree object which represent snapshot of file structure in a commit. It shows files and directories that're part of specific commit or tree object in git repo
- Command :- git ls-tree $commit_id $path
- blob represents a file, tree represents a directory.

![image](https://github.com/user-attachments/assets/d3165fc2-c80c-433b-bab4-5e89701ca4ef)

28. What work is restored when deleted branch is recovered?
- Files which were stashed and saved in stash index list will be recovered back
- Any untracked files will be lost

29. Use of git config
- git uses our username to associate commits with identity
- **git config** :- used to change git config including username
  - **git config --global user.name "name"/ user.mail "email"**

30. What are different branching strategies?
- **master branch** :- main branch for production code
- **feature branch** :- contains feature specific changes merged to master
- **release branch** :- Once developed branch has all features for release we can clone it to release. It is used for next release cycle and no new features are added. Once it is ready to ship, it gets merged with master with version

31. How to check if branch is already merged to master?
- **git branch --merged** :- lists branches merged into current branches
- **git branch --no-merged** :- lists branches not merged to current

![image](https://github.com/user-attachments/assets/d2de4e45-0e42-4027-90ad-6b8792f45c5e)

32. Why it is recommended to create additional commits rather than amending existing commit?
- Amend operation destroys state that was previous saved in a commit. Growth of small commit and acquire unrelated changes

33. What does hook comprises of in git?
- Hooks are scripts that run automatically at certain points in git workflow. They're used to trigger actions before or after certain git events such as commenting, merging, pushing.
- Hooks allows to automate tasks
- Located in .git/hooks within local.

![image](https://github.com/user-attachments/assets/9df37ad5-79b7-4250-8eaa-037f65b37a12)

34. Explain git workflow
- To record history of project, git workflow employs 2 parallel long running branches :- **master and development**
- master branch is for production and hotfix
- development branch is for development of feature

35. Difference between revert and reset
- Reset is used to return entire working tree to last committed state. This scraps commits in private branch or throw away uncommitted changes. It also alters existing commit history
- Revert creates new commit that undergoes changes from previous commits. It adds new history to project, doesnt modify history

36. How to squash last N commits into single commit?
- To squash last N commits into single commit in git, you can use interactive rebase. It allows to combine multiple commits into one while preserving cleaner commit history.
- If we want to write new commit message from scratch :- git reset --soft HEAD N

37. git cherry pick
- Used to introduce particular commit from one branch within repo onto diff branch
- Used to forward or revert commits from maintenance branch to dev branch
- Command :- **git cherry-pick $commit_id**

![image](https://github.com/user-attachments/assets/68ae819b-087e-4392-b010-51607580e4a6)
![image](https://github.com/user-attachments/assets/91c5113a-ca85-4e41-bbaa-c37d231f16da)

38. What are git workflows?
- Git workflow define structure ways for teams to collaborate on software development using git
  - **Centralised workflow** :- All changes are pushed to main/master branch. Developer pull from main branch and commit directly. Not ideal for large teams due to conflicts
  - **Feature branch workflow** :- Each new feature is developed in separate branch. Developers push changes to feature branches and merge them into main branch after approval. It reduces conflicts and keep main branch stable
  - **Gitflow workflow** :- Uses multiple branches like main(for stable prod code), developer(integration branch), feature(for new features), release(for prod release), hotfix(for urgent prod fixes). Its good for projects with scheduled releases
  - **Github flow** :- Work directly from main branch. Create feature branches and open Pull requests(PRs). Merge PRs after review and deploy (Ideal for CICD)
  - **Forking workflow** :- Used in open source projects. Developers fork repo, make changes in the copy and submit PR to main repo. Maintainers review and merge PRs
  - **Trunk based development** :- Developers work directly on main branch . Frequent integration prevents large merge conflicts. Works well with feature flags and CICD
 
39. Git bisect to determine source of bug?
- git bisect is a poweful git command used to find commit that introduced a bug by performing binary search between a known good commit and a bad commit. It automates process of checking commits to pinpoint the first one that introduced an issue.g
- Its a process explained below starting with **git bisect start**

![image](https://github.com/user-attachments/assets/81c70dae-c982-47b8-bb52-4ed6ad9f22fb)

40. git reflog
- git reflog (reference log) is a command that tracks updates to the tip of branches, HEAD and other references, allowing us to recover lost commits, reset branches or inspect recent changes
- **Recover lost commits** :- If you've mistakenly reset or deleted a branch, it helps find commit SHA to restore it

![image](https://github.com/user-attachments/assets/7152bf42-de02-48f4-9a6d-4413dc22c531)

- **View recent branch checkouts and changes** :- git reflog
- **Restore deleted branches** :- If we've deleted branch, find its last commit using git reflog and create new branch from it

![image](https://github.com/user-attachments/assets/3cd12e33-20f0-41cd-894d-9da3e10eb8df)

41. How to recover deleted branch?
- Using git reflog command to get history of commits, identify history stamp
- Use above que

42. What is the purpose of git tags?
- Git tags are used to mark specific points in your git history, often for releases.
- Unlike branches tags dont change, they're permanant references to commits
  - List tags :- git tag
  - View tag details :- git show v1.0
  - Tag specific commit :- git tag v1.0
  - Pushing tags to remote :- git push origin v1.0 (git push --tags to push all tags)
  - Delete local tag :- git tag -d v1.0
  - Delete remote tag :- git push origin --delete v1.0
  - Checkout the tag :- git checkout v1.0


















