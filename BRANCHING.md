
# GIT Branching

- When we create files, do commits they get stored in master branch. When we create local repository, master branch will be created.
- After this whatever no of files are created or commits done are stored in master branch. So it is main branch. All the source code is placed in "master" branch
- Suppose any developer is working on one feature so he will need multiple commits to develop the same. But the code he is working on could be developed to some stage. So what he will do is he will create one branch which will inherit commits and files from master branch without disturbing master branch
  Once that branch is created, developer will switch to that branch and will commit changes.
  Then he can push the entire code or feature to remote repository or he can merge that code to master branch
- So using branching concept, parallel development will happen as multiple developers can develop their code creating branches from master and merge to it without corrupting existing code in master branch
- By this we can have parallel development and clean code without messing it at one branch/place

- But here every branch is isolated means independent. Means files added to sub branches will not be there in master branch and vice versa. This is until we merge the code

**1. git branch**
- To view available branches
- If we get * before branch in output of this command, it shows active branch
- We can also execute "git status" to check branch

**2. git branch $branch**
- To create new branch
- As soon as we create new branch, all files in master branch will be inherited to the new branch

**3. git checkout**
- Switch from one branch to another
  git checkout $branch
- Now branch to which we are switched is active one instead of master

**4. git checkout -b $branch**
- Create new branch and switch to it in one command

![image](https://github.com/user-attachments/assets/3959ca58-e841-464e-81e1-457b2dae905c)
