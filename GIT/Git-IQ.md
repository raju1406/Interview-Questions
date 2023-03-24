### What is Source Code Management?
+ It is a process through which we can store and manage any code. Developers write code,Testers write test cases and DevOps engineers write scripts. This code, 
we can store and manage in Source Code Management.

### How many types of repositories available in Git?
  + There are two types of repositories available in Git Bare Repositories (Central)These repositories are only for Storing & Sharing the code
All central repositories are bare repositories Non – Bare Repositories (Local)In these repositories, we can modify the files 
All local /user repositories are non-Bare Repositories 

### What is GitHub?
+ Git hub is central git repository where we can store code centrally.

### What is git?
+ Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.
  
### How to create a bare repository? 
+ **git init --bare myproject.git** Does not contain any working or checked out a copy of source files Bare repositories store 
git revision history in the root folder of your repository instead of the .git subfolder

### How can you initialize a repository in Git? 
+ If you want to initialize an empty repository to a directory in Git,you need to enter the git init command. After this command, a hidden .git folder will appear in the folder.

### What is a git repository?
+ A repository in git is a place where git stores all the files.Git can either stores the files on the local repository or on the remote repository.

### What is the function of git clone?
+ The git clone command creates a copy of an existing Git repository.To get the copy of a central repository, ‘cloning’  is the most common way used by programmers.

### Git pull vs fetch?
+ Git pull command pulls new changes or commits from a particular branch from your central repository and updates your target branch in your local repository.
``` git bash
$ git pull origin master
```
+ Git fetch retrieves new data from a remote repository but does not integrate it into our working files.It helps in checking if any changes happened in the remote repository. 
It does not manipulate or destroy anything in the process. 
```git bash
$ git fetch –-all
```
### Git clone vs fetch ? 
+ Git clone creates a copy of the code in your local machine. Git fetch , fetches code from git to your local repository but will not update it Once

### What do you mean by “git cherry-pick”?
+ If by mistake, you have committed a change into the wrong branch, you can use the “git cherry-pick” command.This command will allow you to apply commit from one branch to another branch. 
```git bash
$ git cherry-pick <commit id>
```
### Git merge vs rebase?
+ Git rebase and merge both integrate changes from one branch into multiplebranchs.Git rebase moves a feature branch into a master. 
+ Git merge adds a new commit, preserving the history of both development branch.

### What is git push and pull ?
+ Push - pushing sends the recent commit history from your local repository up to GitHub.
+ Pull - a pull grabs any changes from the central repository and merges them into your local repository.

### What is Git stash?  
+ We create multiple branches to work simultaneously on multiple features. But to work on multiple tasks simultaneously in one branch, 
we use git stash. Stash is a temporary repository.

### Difference between Git pull and Git clone?
+ Git clone is to get whole copy of central repository Git pull is to get only new changes from central repository (Incremental data)
### what is git config and git config --global?
+ Run git config --list , showing system, global, and (if inside a repository) local configs.

### What is git add ?
+ git add : Open the terminal. Change the current working directory to your local repository.

### What is git commit ?
+ git commit:Commit the file that you’ve staged in your local repository.$ git commit -m "Add existing file"
