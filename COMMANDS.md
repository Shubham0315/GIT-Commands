# GIT Commands

- We can use linux commands for git
- Create a directory on system and go into it. Open GIT CLI. Create a file there
- To configure user and email for user:-  **git config --global user.name "Shubham315" and git config --global user.email shubhamr0315@gmail.com**
- To view configured assets :- **git config --list**

  ![image](https://github.com/user-attachments/assets/8a4b379b-0125-47f5-9627-c16dc3d2b097)

**1. git init**
- It create/initializes one empty git repository named ".git". In linux it represent hidden files.
- When we check these files in workspace we cannot see that as they are hidden. Go to view pane(ls -a) and show hidden. So here local repository is created for workspace
- This is needed to enable version control for specific project/folder
- .git folder is hidden one which is responsible for all the activity inside our repository

![image](https://github.com/user-attachments/assets/d14921e6-c883-4827-9fef-f55835079caf)

**2. git status**
- Shows tracked/untracked files
- Untracked means available in workspace but not added to staging/local (in 1 but not in 2)
- If any file is unstaged, it shows here is one empty file. If file is complete and to consider it "git add"

**3. git add**
- git add $f1 $f2 or git add . (. means all files)
- Adds files from workspace to staging area which is a check for extra precaution
- git add -a --> adds all files to staging
- After added to staging if we check status, we can see them as tracked files. File gets staged and tracked now. These files are ready to get committed to local

![image](https://github.com/user-attachments/assets/0d47c8e3-7331-46de-9876-6e79ebc78b0c)

**4. git commit**
- Git commit is a command in git that captures snapshot of project's currently staged changes creating a permanent record in repository's history
- Before committing to local, we have to use some configuration commands
- git config --global
  global --> User name and email will be applicable for all git repositories which we are creating for local machine
- Command :- git commit -m $Message
- After committing, we can check git status, where we see nothing to commit. Working tree is clean. This means all files in workspace are moved to local repository

![image](https://github.com/user-attachments/assets/5484acb8-85ed-4109-a8cc-069b87d8e7e6)

**5. git log**
- To check how many commits are there earlier (commit id, date, comment)
- We can check which user has committed which changes (use of git config) along with commit message

![image](https://github.com/user-attachments/assets/3a1e2a7b-271f-4883-8a48-c7466929672c)

**6. git add + git commit**
- Now if we have modified files in workspace, they will not be there in local with modified content unless they are committed to local. And if we check git status, we can see them as modified
- Here by normal workflow, we could have added them to staging and committed to local
- But these files are not new just modified so they are already tracked in earlier add/commit
  git commit -a -m "Comment"  (-a add to staging) 
- This command used only for tracked files

![image](https://github.com/user-attachments/assets/0a8e8985-7e7d-428c-8fe1-0bf78a37ce5a)

**7. git rm**
- Create 2 files in our system repo and stage just one of them (git add)

![image](https://github.com/user-attachments/assets/2a9db1e4-569f-42a1-90fa-5c49cd495939)

a. Remove files from staging and workspace 
	Command :- **git rm $file**   --> then we can ls and git ls-files to check status in staging and workspace
	
	To remove all files from staging and worskpace --> git rm -r .
![image](https://github.com/user-attachments/assets/6a334c04-f147-4cae-8db3-337e3db61211)

b. Remove file only from staging
	Command :- **git rm --cached $file**
![image](https://github.com/user-attachments/assets/ad8b3603-077c-4ad9-b597-d34ec37f1b59)

c. Remove file only from workspace
	Command :- **rm $file**
![image](https://github.com/user-attachments/assets/5b4eac15-2dc7-4b07-b3b0-f1d8d31db3bc)

**8. git diff**
- Used to compare files between any of the 4 stages of VCS (Workspace, staging, local, remote)
- If we append the staged file in local so before staging it we can check diff for the exact added/removed content

  - **Scenario 1 :- To check diff between files in workspace and staging**

    - Create new folder (SampleProject), create sample index.txt in that using vi
    - This file will be their in your workspace 
    - Now we can initialize empty git repo for this file
    - Now we have to add this file into staging area using git add, check status using git status
    - Now the file in ur workspace will be there in your staging area

    ![image](https://github.com/user-attachments/assets/924a33cb-0ece-446e-ab5a-789295b4dc1a)

    - Now if we edit the file in our workspace those changes will not be there in staging (check using git status)
    - Here we can check diff between workspace and staging using :-  **git diff $file**

    ![image](https://github.com/user-attachments/assets/c9112eaf-9958-4fda-868e-5a612c1449ef)

  	- a/index.txt is target ()
	- b/index.txt is source (staging)
 	- cf6e18b hash of file content from source (staging)
	- ddf1f36 hash of file content from target (workspace)
	- 100644 git file mode ( 100 represents type of file and 644 is permissions)
  	-  --- a/index.txt --> source files missing some lines (staging)
	- +++ b/index.txt --> new lines added in destination file (workspace)
 	- -1 --> in staging we have only one line ( - means source)
	- +1,2 --> in workspace we have 1 extra line and total 2 lines ( + means target)

  - **Scenario 2 :- To see difference in file content between working directory and last commit**
  
     - Now lets commit the staging file in local repo and then check diff between local and workspace
     - $ git commit -m "file commit file contain 1 line" --> staging file will move to local
     - Now add some text to workspace file and then comapre diff between workspace and local (Last commit is always represented using HEAD keyword)
     - git diff HEAD index.txt --> head is latest commit in local and index.txt is file in workspace we're comparing with
 
  ![image](https://github.com/user-attachments/assets/8c621ef8-18ce-4e20-b399-5698e2edcadb)

  - **Scenario 3 :- To see differnce between file in staging area and last commit**

     - Add the workspace content to staging using "git add ."
     - Then we execute --> git diff --staged HEAD index.txt

  ![image](https://github.com/user-attachments/assets/6207f272-0cbc-40ae-8db0-8c760397de12)

  - **Scenario 4 :- To see the difference in file content between specific commit and working directory copy**

     - Commit the staging updated file into local
     - The latest commit is represented by HEAD (above line), the first commit will contain 1 line only while latest have 3 lines
     - Add one more line to workspace so worskpace have 4 lines and local have 3
     - Lets compare file in workspace and 1st commit. 
     - For this we need commit id's of first commit :- git log --oneline

     - Once we know the commit id of first commit :-  **git diff $id $filename**
							$ git diff bba2ee1 index.txt

 - **Scenario 5 :- To see the Difference in file content between specific commit and staging area copy**
      
     - Take same commit id from Scenario-4
     - Command :- **git diff --staged $commit**
     - Here we dont need to give filename in command as it will compare staged file with commit id

 - **Scenario 6 :- To check difference between two specific commit**
 
     - Command :- **git diff $commit1 $commit2 $filename**

**9. git checkout**
- We could have used git show here but having multiple files and if we need all file details from previous commit, its not feasible using "**git show**". So git checkout is useful here
- Also git show can work for small files so as to read on terminal. For 1000s of line of code, its not good.
- Used to **discard unstaged changes in the tracked files of working directory**
- Until and unless files are not added to staging or local repository, they are untracked. At least once the file in workspace is added to staging or local, then it is tracked
- Unstaged changes means the changes which are part of workspace are not in staging area
- Git checkout command is used only for workspace. Basically checkout means undo

e.g :-  
	- Create one file and add some lines and then initialize the same. Add it to staging and commit into local. Now the file is tracked
	- Now make some changes to file in workspace. So staging and local wont have updated changes (unstaged changes)
	- Now to discard these unstaged changes (checkout) :- **git checkout --file**
 	- Checkout is used only for tracked files not untracked ones
![image](https://github.com/user-attachments/assets/7afaf1d2-1185-47e8-b964-d17ae24ffbf9)
![image](https://github.com/user-attachments/assets/7e89fddb-411e-447f-8af5-2a9d63175465)

- If we've multiple commits in a file and want to go back to commit #1
  Command :- **git checkout $CommitID1 -- file**
- Again if we want to go back to 2nd commit
  Command :- **git checkout master -- file** (master as it is head commit for specific branch)

 ![image](https://github.com/user-attachments/assets/615956fa-7cc6-41de-a65d-844e22d3964a)

**10. git reset**
- To remove changes from staging area which are unwanted. To undo commits at repository level (staging to local commits undo operation)
- It is opposite of git add command

![image](https://github.com/user-attachments/assets/f68df5c8-c112-43a9-92fc-4837fd229e7b)

- To undo changes at repo level :- **git reset <mode> <commit id>**.
- Mode will decide whether the changes are gonna be removed from staging area and working directory or not

- a. reset with --mixed mode
  - It is default mode
  - To discard commits in local and staging area. It wont touch workspace
  - When we discard changes from local it will discard them from staging as well 
  - Command :- **git reset --mixed $(commitId-1)**
  - Here whichever commit we have to remove from local/staging, provide the previous commit id of that to the command. So it will remove any new commits above that commit.
  - Even if the file is removed from staging/local, it will be available in workspace as it will not touch there.


![image](https://github.com/user-attachments/assets/68db5162-d791-4f87-bede-5ce0649c60d2)

- b. reset with --soft mode
  - Exactly same as --mixed options. But when we discard changes from local, changes are available in workspace and staging. Means it wont touch staging and woskspace
  - As changes are already present in staging area, we just have to use commit to revert back
  - Command :- **git reset --soft $(commitId-1)**

![image](https://github.com/user-attachments/assets/668d54a9-a240-4c46-a230-9ca6c9a22483)

- c. reset with --hard option (very dangerous)
  - Works same as --mixed except changes will be removed from everywhere (local, staging, workspace)
  - It is impossible to revert back so take care while using it
  - Command :- **git reset --hard $(commitId-1)**

![image](https://github.com/user-attachments/assets/5bd697c0-e878-45e6-a5db-92fce84d8ed7)


11. git show
- 


