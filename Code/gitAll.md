# GIT

## What's GIT?
A code versioning tool, i.e. basically a tool to make backups and keep a history of them, while allowing you to share your code, which greatly facilitates teamwork.

## Principle of GIT
- The code is online on the platform we use (github, gitlab, gitea, etc). We download (= `clone`) a copy that we can modify, then we upload the modifications

- You don't lose your code if the SSD crashes

- Since the changes are online, the other members of the team just have to download (= `pull`) the latest changes

- To indicate that we are going to use a folder with git, we use the `git init` command, which allows us to use the different git commands

- REMOTE <==> LOCAL

## Installation

To be able to use GIT, you must first download, install and configure GIT on your computer :

##### <ins>WINDOWS</ins> :
   - Download GIT : https://git-for-windows.github.io/
   - Install GIT : Launch the executable
   - Configure your account : 

    git config --global user.name "[YOUR NAME]" 
    git config --global user.email "[first-name].[last-name]@ynov.com"
    
##### <ins>MAC OS</ins> :
If you're working with MacOS, it's possible that you already have GIT installed (with XCode).
So you can test into your terminal : 

    git --version

If you get an output like `git version 2.29.2`, then you have GIT installed. 

But if you don't have anything on the screen, do the following steps:

###### With Homebrew : 
    brew install git
    
###### Without Homebrew (dmg file) : 
   - Download GIT : https://sourceforge.net/projects/git-osx-installer/files/
   - Install GIT : Use the `.dmg` file
   - Configure your account : 
   
    git config --global user.name "[YOUR NAME]" 
    git config --global user.email "[first-name].[last-name]@ynov.com"
 
##### <ins>LINUX</ins> :
   - Open your terminal and write this command : 
   
    sudo apt-get update 
    sudo apt-get install git
  
   - Configure your account : 
   
    git config --global user.name "[YOUR NAME]" 
    git config --global user.email "[first-name].[last-name]@ynov.com"

## Start with GIT : 
You have two solutions to start working with GIT, [create a repository on a GIT server] and clone on your workstation this existing repository OR create a folder locally, on your workstation, initialize GIT and push it on the GIT server.

##### <ins>From a GIT server</ins> :
- Create a repository 
- Copy the https or SSH link (for SSH, you have to configure your account on the GIT server with your generated SSH key)
- In your terminal (to the desired path) : 
    
      git clone https://git.ytrack.learn.ynov.com/FLASTNAME/my-repo.git
This command will create a repository `my-repo` linked with your GIT server
      
- Let's play!
      
##### <ins>From your workstation</ins> :
- Create a folder on your workstation (ex: my-app)
- Open a terminal into your new folder

      git init
This command will create a `.git` hidden subdirectory that contains all of your necessary repository files.

    git add --all
This command will tell GIT to track all files and directories contains in the folder.

    git commit -m "initial commit"
    git push origin master
These commands will create a commit with the message `initial commit` and push it to the GIT server.
- Let's play!

## Commands

#### commit
- The commit is the basis of git. What we call a `commit` is the fact of saving your code at a given time.
- The interest is first of all to be able to go back to a previous functional version of the code, if ever the code is broken, the project is not to be thrown away.
- The other advantage is to break down your code into small features, which allows you to :
    - 1: know where you are
    - 2: know where you are going
- To do a `commit` : 

      git commit -m "your commit message"
      
- Please, don't write dirty messages. A commit message will help you and your team to manage your code.
    - Some exemples : `add authentication` | `fix routing redirect after logout` | `if you read this, sing 'we will rock you' and I'll buy you a beer`
- A `commit` is a LOCAL backup on your machine, to put the code online, safely, you have to do what we call a `push`.

#### push
- A `push` is the fact of deploying the code, of putting it online on a remote server.
- A `push` only uploads the commits you have made.
- To do a `push` : 

      git push [remote][branch]
- Exemple : 

      git push origin master

#### remote
- A `remote` is simply a server on which we will push our code.
- To add a `remote` : 

      git remote add [name-of-the-remote][server-link]
- To remove a `remote` : 

      git rm [name-of-the-remote]
- Exemple : 

      git remote add origin https://git.ytrack.learn.ynov.com/FLASTNAME/my-repo.git
      
#### fetch & pull
- `git fetch` command downloads commits, and files from a remote repository into your local repo, without overwriting your changes, I.e it has no effect on your local development work. 
- You can consider `git fetch` the `safe` version to keep your local repository updated. It will download the remote content, but not update your local repo's working state, leaving your current work intact. 
- `git pull` is the more aggressive alternative; it will download the remote content `git fetch` for the active local branch and immediately execute `git merge` to create a merge commit for the new remote content. If you have pending changes in progress this will cause conflicts and kick-off the merge conflict resolution flow.
- After a `git fetch`, you have to `git merge FETCH_HEAD`

- To do a `git pull` : 

      git pull [remote][branch]
      
- To do a `git fetch` : 

      git fetch
      // And when you want to merge...
      git merge FETCH_HEAD

#### stash
- git stash temporarily shelves changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. Stashing is handy if you need to quickly switch context and work on something else, but you're mid-way through a code change and aren't quite ready to commit.
- To do a `stash` : 

      git stash
- To retrieve your code : 

      git stash pop

#### status
- The git status command displays the state of the working directory and the staging area. 
- It lets you see which changes have been staged, which haven't, and which files aren't being tracked by GIT.
- To see the `status` : 

      git status
      
### branch
- During the development of a project, you will create features, solve bugs, test on environments and collaborate in teams. All good reasons to use branches.
- The default branch of a project is `master`

      A---B-----------H------------ ← master
           \         /
            C---E---G---I ← dev
             \ / \ /
              D   F
              
- To create and work on a `branch`, two ways :

      git branch [branch_name]
      git checkout [branch_name]
      
      OR
      
      git checkout -b [branch_name]
      
- Tips #2: Name your branches in a smart way : 
    - For a feature: `feat(feature_name)`
    - For a bugfix: `bugfix(bug_name)`
- Tips #2: If you use a board with tickets, use the number of your ticket in the name of your branch : 
    - Exemple : `feat(423/auth)` | `feat(32/login)`
    - This will help you enormously in the organisation of your project!

# You should look at : 
- `git rebase`
- `pull request`
- `gitflow`
- ...
