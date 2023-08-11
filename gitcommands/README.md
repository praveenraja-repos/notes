**Git help:**
|Git Command | Explanation |
|---|---|
|git help config | option 1 |
|git config --help | option 2|

<br/>
<br/>
**Git configuration:** 

|Git Command | Explanation |
|---|---|
|git config --global user.name "property value" | add or update the values in git configuration |
|git config --list |list all the existing configuration key value pair |

```
git config --global credential.helper store
```

<br/>
<br/>


**Adding existing project to git**
```
git remote add origin <Remote path>

or

git remote add set-url <remote path>
```

-git remote add origin https://git.smaple.com/scm/prod/project-residency.git

---
      
**Important git commands:**
```
git remote add <local_repo> <repo_name>
```
- Add new local repo to the remote repo
- Eg: git remote add origin https://gitlab-ce.apps.oxygen.emea-1.rht-labs.com/aaat/flight-search.git
---
```
git remote rename origin old-origin
```
-  Rename a repo name. 
- Once it is rename you need to add the renamed repo to remote repo using the above command.
- Eg: git remote rename origin old-origin
---
```
git clone <url> <where to clone path>
```  
- clone an existing project from the remote repo to local repository 
- eg: git clone <http://:full path.git> .
---

```
git init  
```
- To add existing project folder to local git repo 
- It will create a new folder called `.git`
---
```
git fetch --all  
```
- To fetch the latest updates from the remote repository, including all remote branches.
---
```
git commit -m "<messages>" 
```	
- This will move all the files in the staging area to local repository 
---
```
git pull <remote-repo-name> <branch-name> 
```
- pull data from different remote repo and branch name
- EG: git pull origin master 
---
```
git branch <branch-Name> 
```
- Will create a branch in local repository
---
```
git branch 
```
- Will list all the branch locally available including remote branch which are checked out 	
---
```
git push -u <remote-repo> <remote-branch-name> 
```
- -u will associate the local branch to remote branch once it is associated , from next time only git push and pull will work 
---
```
git merge <local-branch-name> 
```
- This will merge the specified branch to the current branch. 
---
<br/><br/>
    
**Git Checkout:**
```
git checkout <branch-name> 
```	
- will switch the current working branch to the specified branch 
---
```
git checkout <file-name> 
```
- It will revert your local change 
---
```
git checkout -b <new branch name> 
```
- creating a new branch and check out with same command 
---
```
git checkout <first 6 char of commit hash> 
```
- Will make the working area to that commit. from there a new branch can be created and continue working on it. 
---
<br/><br/>
    
**Git Add:**
```
git add <filename/directory> 
    or  
git add -A 
```
- -A will add all the files to the staging area 
- This is for new files and for modified files 
---
```
git add -u 
```
- It will add all modified and updated files but not the untracked files and new files 
<br/><br/>
    
**Deleting a branch:**
```
git branch -d <local-branch-name> 
```	
- will delete the local branch 
---
```
git push origin --delete <branch-name> 
```
- will delete the remote branch 
---
`.gitingore` is a file which will have list of file name with wildcard "*". These file will not be shown in add file or change list 
---
<br/><br/>
    
**Amending a commit comment**
```
git checkout <file-name> 
```	
- It will revert your local change 
---
```
git commit --amend -m "new message to be updated" 
```
- This will update the comment on the last commit. 
---
<br/>
<br/>

**Git Chery pick:**
```
git cherry-pick <commit hash id> 
```	
- will move commit change form one branch to the current branch with a new commit.  
- Old commit will still exist  
<br/>
<br/>
    
**Git reset**
```
git reset <filename> 
     or  
git reset 
```	
- Without file name will remove all the files from staging area 
---
```
git reset --soft <first 6 char of commit hash>  
```
*Reset Soft:* 
- This will remove the commit from the remote and bring the commit to our local stage area. 
- After soft reset, git status will show the changes in staging 
---
```
git reset <first 6 char of commit hash> 
```
*Default reset(mix):* 
- This bring all the to the working area not to the staging area 
---
```
git reset --hard    
```
*Git reset hard:* 
- Will remove the commit changes.  
- Changes will not be there in staging or local 
---
```
git clean -df 
```
- This will clean all the untracked files in the working area 
- -d will clear all the untracked directories 
- -f will clear all the untracked files 
---
 <br/>
<br/>
    
**To see the information:**
```
git log 
```	
- To see all the commits 
---
```
git reflog 
```
- It will show all the action (amend, cherpick, reset, etc) in the same order 
---
```
git status 
```
- Will show what are the files need to be added and files that are need to be committed 
```
git remote -v 
```
- Get the remote repo urls 
---
```
git branch -a  
```
- Will list all the local and remote branches 
---
```
git diff 
```	
- Will list the files and the changes that are done locally 
---
```
git diff <commit ID 1> <commit ID 2>  
```	
- Will show the difference between these two commits 
---
<br/>
<br/>
    
**A general Commit process:**
```
git branch <local-branch-name> 
```	
- create new feature branch from current working area 
---
```
git checkout <local branch name> 
```	
- Switching to the newly created branch 
---
```
git status 
```	
- Just check the file status 
---
```
git diff 
```
- Verify all the change and the files to be committed 
---
```
git pull origin master 
```
- Pull all the changed from remote to local feature 
---
```
git add -A 
```	
- Add all the changed file to the stage 
---
```
git commit 
```	
- Commit the staged files to the local branch 
---
```
git push -u origin <branch name> 
```	
- Pushing and linking the current staged change to the remote branch 
---
<br/>
<br/>
    
**Git revert**
```
git revert <first 6 char of commit hash> 
```	
- Revert the specified commit and it will do a new commit  removing that changes. 
---
<br/>
<br/>
    
**Git Stash**
```
git stash save "comment for our reference" 
```	
- This will  save all the working area change to the stash area 
- Working area will be equal to the remote branch 
---
```
git stash list 
```
- Will list all the stash with an ID 
---
```
git stash apply <stash id> 
```
- Will bring the change to the working area 
- Stash which is applied will be still available in the stash list 
  - EG: git stash apply stash@{0} 
---
```
git stash pop 
```	
- Will apply the very first stash change to the working area 
- It will remove the stash from stash list  
---
```
git stash drop <stash id> 
```
- Will remove the particular stash form the stash list 
---
```
git stash clear 
```
- will remove all items from the stash list 
---
<br/>
<br/>
    
**Git Rebase vs merge:**

    Rebase will move all you commits from feature branch to master branch where merge will combine all commits and update one changes into the master branch. 
```
git rebase master
```
- This will move your base of your feature branch(current checked out branch) to the head of the master 
- At this time, git will merge all the latest changes to  you feature franch  

 
	

 
