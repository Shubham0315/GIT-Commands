# GIT Merging

- The source code will be there in master branch
- When we do parallel development, we create new branch (feature branch) from master, commit code in the newly created branch and then merge changes from feature branch to master branch. This is "Merging"

Fast Forward Merge
-
- Suppose we created a child branch from master branch which have 2 commits and added two commits there. And then we merged the code from feature branch to master
- Here from creation of child branch to merging, if no commit happens to master branch then it is "Fast Forward Merge". So at the end, the master branch will have only 4 commits, 2 before child creation and 2 in child which are merged
- In short, in this method, we only do changes in child/feature branch not in master. No commits will be done in master after creation of child. So by this, there are no chances of getting any conflicts in code

**DEMO**
- Create new empty repository and initialize it (master branch). Add 2 files and stage,commit them. So master branch will have 2 files and 2 commits. (Add and commits should be one by one)

![image](https://github.com/user-attachments/assets/8e6495a9-8732-4b64-adce-39f5af56b70c)
![image](https://github.com/user-attachments/assets/7a2ff261-7eb9-4201-81d1-9a3081897e03)

- Create new branch "feature". Add 2 files and stage, commit them. So child branch will have 4 commits and 4 files in total. (Add and commits should be one by one)

![image](https://github.com/user-attachments/assets/04656b56-a45b-4db7-88f3-48feff893caa)
![image](https://github.com/user-attachments/assets/690a0b84-68b5-4b5a-a260-a4107baf5c15)
![image](https://github.com/user-attachments/assets/d57b1b5c-60b3-474a-9940-11c7c35f1dfe)

- Now to execute merge command, first switch to master branch. Command will always execute through master branch
  Command :- **git merge $featureBranch**
- When command is executed, if no conflict is there, we can see fast-forward in output
- In fast forward, the last commit in child will get there in master when merged and it will reflect that as well. Latest commit in master will be last commit in child

![image](https://github.com/user-attachments/assets/b4020493-3fbc-45c2-98c0-7fc168682edb)


Three Way Merge
-
- Here parallel development will happen in master and child branch
- Suppose we created a child branch from master branch which have 2 commits and added 2 commits in child branch. And then merge the code from child to master. Parallely, if we commit changes in master branch.
- There will be chances of conflict here as some changes in master (after 2nd commit in master) may not be there in child or some commits in child (after 2nd commit in child) may not be there in master when merged at the end. Or the file in master before creation of child gets modified in feature branch (some lines added), it can be conflicting once merged to master
- When we merge code from child to master at the end, it creates "merged commit" which auto adds any new commit in master (after creation of child) to the merged commit from child. There can be conflicts in merged commit that we have to resolve manually.

**DEMO**
- Create new empty repository and initialize it (master branch). Add 2 files and stage,commit them. So master branch will have 2 files and 2 commits. (Add and commits should be one by one)

![image](https://github.com/user-attachments/assets/1bdce23f-0c10-4729-a3d7-947464a0a70b)
![image](https://github.com/user-attachments/assets/d8289072-d0e5-40c0-8a49-205c2a85f17c)

- Create new branch "feature". Add 2 files and stage, commit them. So child branch will have 4 commits and 4 files in total. (Add and commits should be one by one)

![image](https://github.com/user-attachments/assets/f4dcbcce-9191-4fbd-b1ae-7cdf2c16971b)
![image](https://github.com/user-attachments/assets/20d72dc8-c35c-4991-9ced-fb7d323fc821)
![image](https://github.com/user-attachments/assets/b7971ff7-618c-4e7e-b3e4-75c5f1bd1ebb)

- Now switch back to master and add new commit. There will be 3 files and 3 commits in master

![image](https://github.com/user-attachments/assets/78820041-3292-49fd-a6d1-6eab1a0965f9)

- Now we have to merge the changes in master.
- When we do "**git merge $feature**" it will open vi editor. Save file using :wq!. Then after pressing enter, we get merged by recursive strategy/ort strategy which shows **three way merge**.
- We can resolve conflicts in master branch and then merge child branch into it. As soon as we merge the latest commit to master, it will create a new commit

![image](https://github.com/user-attachments/assets/9ef2586f-4420-4149-8522-853aaad2d0d7)
![image](https://github.com/user-attachments/assets/3c63b9ae-d75f-436f-8b8d-7a5dc96be4a9)


