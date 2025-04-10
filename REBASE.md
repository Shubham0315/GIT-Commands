# GIT Rebase

- In 3-way merge, when we merge feature branch in master, new merge commit is created. **3 way is non-linear** while **fast forward is linear**
- In fast forward merge, for every commit there will be only one parent commit. In 3 way merge, there can be possibility that there will be multiple parent commits for every commit

- Rebase is applicable for only fast forward merge. Rebase is alternative of merge command

- In reabse no merge commit is created but in 3 way new merge commit is created

**Rebase is 2 step process** :- Add feature on top of master and Merge feature to master branch


Add feature on top of master
-
- We will add(rebase) feature branch on top of master and then we will merge the feature branch with master  (2 step process)

- Lets have 2 commits in master (C1M and C2M) and then create feature.

![image](https://github.com/user-attachments/assets/eb19af61-f7ac-4b6c-8711-1af808d020e5)
![image](https://github.com/user-attachments/assets/3ed5c8be-48fa-4559-8759-2dacdf7f84c4)

- Have 2 commits (C1F and C2F) in feature as well

![image](https://github.com/user-attachments/assets/00a229a9-4025-47b7-b887-c8edb23b0ec8)
![image](https://github.com/user-attachments/assets/26e041d5-2470-40dd-864e-aa2f5e0a64ae)
![image](https://github.com/user-attachments/assets/17660120-f757-4b8c-89c3-ff6823935d9a)

- Add one more in master (C3M) after creating feature (separate)

![image](https://github.com/user-attachments/assets/08caae20-e37b-4826-97c9-b9da2e80224c)

- When we execute "git rebase master" **(executed from feature)**,  Git internally creates 2 new commit objects for the two commits in feature branch
- And then 2 commits in feature branch will be discarded as new objects will have same data as earlier commits. These 2 new commit objects will be created on top of "master" (just like below SS_

![image](https://github.com/user-attachments/assets/05b83b8e-1dfd-47fb-99d6-6f1f3e4e97ab)

- When we create feature C2M is base commit, but when we rebase feature to master, C3M will become your base commit

Merge feature to master branch
-
- Command :- **git merge feature**

![image](https://github.com/user-attachments/assets/a620a4aa-7050-4a02-95d1-c49b89a60da6)

- When rebase is used, there are no chances of getting conflicts

- Disadvantage :-  It is difficult to determine which changes are from which branch as branches are added and merged and commits in feature are removed

? When to go for merge and when rebase?
-
- Everytime we can go for merge whether there are conflicts or not. After merging and resolving we can push to remote. In normal merge, history is also preserved
- Rebase can be only used within local. Only you are responsible for your changes and can create multiple branches and rebase them as needed.
  So advisable not to use rebase for remote repository as multiple developers can be using the master branch. In rebase history is not maintained as feature gets vanished

- Only if you want to follow linear, then go for rebase

