# GIT Commands

- We can use linux commands for git
- Create a directory on system and go into it. Open GIT CLI. Create a file there
- To configure user and email for user:-  **git config --global user.name "Shubham315" and git config --global user.email shubhamr0315@gmail.com**
  To view configured assets :- **git config --list**

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
  -
  
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
  -

     - Now lets commit the staging file in local repo and then check diff between local and workspace
     - $ git commit -m "file commit file contain 1 line" --> staging file will move to local
     - Now add some text to workspace file and then comapre diff between workspace and local (Last commit is always represented using HEAD keyword)
     - git diff HEAD index.txt --> head is latest commit in local and index.txt is file in workspace we're comparing with
 
  ![image](https://github.com/user-attachments/assets/8c621ef8-18ce-4e20-b399-5698e2edcadb)

  - **Scenario 3 :- To see differnce between file in staging area and last commit**

     - Add the workspace content to staging using "git add ."
     - Then we execute --> git diff --staged HEAD index.txt

  ![image](https://github.com/user-attachments/assets/6207f272-0cbc-40ae-8db0-8c760397de12)

  
