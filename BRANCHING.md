# GIT Branching

- When we create files, do commits they get stored in master branch. When we create local repository, master branch will be created.
- After this whatever no of files are created or commits done are stored in master branch. So it is main branch. All the source code is placed in "master" branch
- Suppose any developer is working on one feature so he will need multiple commits to develop the same. But the code he is working on could be developed to some stage. So what he will do is he will create one branch which will inherit commits and files from master branch without disturbing master branch
  Once that branch is created, developer will switch to that branch and will commit changes.
  Then he can push the entire code or feature to remote repository or he can merge that code to master branch
- So using branching concept, parallel development will happen as multiple developers can develop their code creating branches from master and merge to it without corrupting existing code in master branch
- By this we can have parallel development and clean code without messing it at one branch/place

- But here every branch is isolated means independent. Means files added to sub branches will not be there in master branch and vice versa. This is until we merge the code

