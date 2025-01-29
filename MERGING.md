# GIT Merging

- The source code will be there in master branch
- When we do parallel development, we create new branch (feature branch) from master, commit code in the newly created branch and then merge changes from feature branch to master branch. This is "Merging"

1. Fast Forward Merge
- Suppose we created a child branch from master branch which have 2 commits and added two commits there. And then we merged the code from feature branch to master
  Here from creation of child branch to merging, if no commit happens to master branch then it is "Fast Forward Merge"
  So at the end, the master branch will have only 4 commits, 2 before child creation and 2 in child which are merged
- In short, in this method, we only do changes in child/feature branch not in master. No commits will be done in master after creation of child.
- So by this, there are no chances of getting any conflicts in code

2. Three Way Merge
- Here parallel development will happen in master and child branch
- Suppose we created a child branch from master branch which have 2 commits and added 2 commits in child branch. And then merge the code from child to master.
  Parallely, if we commit changes in master branch.
  There will be chances of conflict here as some changes in master (after 2nd commit in master) may not be there in child or some commits in child (after 2nd commit in child) may not be there in master when merged at the end.
  Or the file in master before creation of child gets modified in feature branch (some lines added), it can be conflicting once merged to master

- When we merge code from child to master at the end, it creates "merged commit" which auto adds any new commit in master (after creation of child) to the merged commit from child. There can be conflicts in merged commit that we have to resolve manually
