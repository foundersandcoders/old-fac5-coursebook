# Gitflow

##what is the difference between git and gitHub?

 Git is a version control system. A version control system lets people build software collaboratively without getting in each other's way.  

 GitHub is an online storage service that makes it easy to backup and manage all the different versions of a project. GitHub uses Git but they are not the same thing. There are other service just like Github that do the same thing (like Bitbucket and Kiln). All these services use Git.

 All Git does is give you a history of all the different versions of a piece of software. Every time you write code and save it you create a new version of the software.

 Having every version of a piece of software is useful when you are working with other people because it lets you see if anyone else has made any changes to the software since you last worked on it. 

 You can also merge versions together. Conflicts can then be resolved when you merge similiar versions. 

 You can also go back to a previous version if you ever break something.

 All useful stuff when collaborating.

 If you want to use git you will need to install it on your computer first.

 + If you are using a mac, the easiest thing is to install git with [Homebrew](http://brew.sh/). 

 + Windows use [http://git-scm.com/download/win](http://git-scm.com/download/win). 

 + Linux install using these instructions [http://git-scm.com/download/linux](http://git-scm.com/download/linux).

##Why use a git flow? And how does this help with resolving conflicts?

 A git flow is a standardised route for information that enables a team to work together on a single repository. Without a git flow, team members are likely to lose work, overwrite the work of others and so on. Resolving conflicts between different versions of files takes a significant amount of time, and working to the git flow minimises wasted effort across the team.

 A proper git flow results in each team member being able to compare their working files stored on their computer with the most up to date version of the repository _prior_ to pushing files to github.

 The basic path of information is:
 *Master Branch (GH)
 *Master Branch (Local)
 *Own Branch (Local)
 *Own Branch (GH)

 The cardinal rule is that no-one pushes updates to the GH master branch from any local folder.

 The basic steps to setting up a successful git flow:
 1. Someone _creates_ the main git repo (GH Master
 2. *Everyone* _creates_ a branch of the master branch (GH Branch)
 3. All team members _clone_ the master branch to their computer (Local Master)
 4. All team members _create_ a personal branch where they can work on files (Local Branch)

 The basic way to work through the flow (commands in italics)
 1. _Pull_ the master from GH Master to Local Master
 2. _Pull_ the master from GH Master to the Local Branch
 3. Work on files in Local Branch
 4. When ready to _commit_ changes to GH Branch, _move_ to Local Master and _pull_ GH Master files to Local Master
 5. _Move_ to your Local Branch and _merge_ Local Master with Local Branch
 6. Use your text editor to resolve any conflicts and save files, see below for more.
 7. _Add_ and _commit_ files in your Local Master
 8. _Push_ your work to your GH Branch
 9. Create a _pull_ request on Github to compare the GH Master with your GH Branch
 10. A *different* team member should review this pull request and either accept or reject it.

 Tips:
 *Communicate with your team
 *Use lower case letters for everything in filenames
 *Be as detailed as possible when identifying the contents of a commit
 *Try to have as few people working on the same file as possible (preferably 1!)
 *When using Harp on github, gh-pages should be treated as the GH Master
 *The person looking after to repo still has to work from their own branch in git hub
 *Think about breathing in (data) through the master branch, and breathing out (data) through your local branches
 
##Resolving Conflicts

 You have to resolve conflicts using a text editor. This will happen, and is generally annoying. The idea of git flow is to minimise the number of conflicts that you will have to resolve, but ultimately they are unavoidable.

 When a conflict arises, git will create a single text file including the non-conflicting material in the two conflicting files, as well as the conflicting material surrounded by <<<<<< and >>>>>>

 Git uses ========= to separate the two conflicting sections of text, so you can compare them easily.

 Resolve conflicts by using a text editor and changing the requisite files, selecting whatever text you wish to keep. Just saving the file will leave the separators and dual pieces of text in the file itself. You can't resolve merge conflicts on github, so if you find one occurs when merging GH Branches to the GH Master, you will have to pull the existing GH Master down to your Local Master, and resolve the conflict when you merge this with your Local Branch.

##What are some new helpful git commands that could improve your work flows?

# Some helpful git commands

## git clone [address.git]

Hopefully you know this one - creates a folder on your local machine and clones the repository at [address.git] into it  

## git branch  

Checks which branch you're on  

### git branch [name]  

Creates a branch named [name]  

## git checkout [branch]  

Switch to branch [branch]  

### git checkout -b [branch]  

Create new branch [branch] and switch to it  

## git status  

This "displays the state of the working directory and the staging area" - which basically means it lets you see the changes you've made, whether they've been staged or not, and which files are/aren't currently being tracked. NB - this doesn't show you anything about the project history, just the current status  

## git log  

Haven't used this yet, but likely to be useful - shows project history  

## git add [filename]  

Adds changes in the working directory to the staging area. If you specify a filename, changes to that file will be staged for the next commit. If you have a full stop instead of filename, it adds all files with changes  

## git commit -m "message"  

Commits the versions of your changed (and already added) files to the project history. You need to add a message explaining your commit, and using -m means you can write the message in right there, rather than having to use a text editory etc.  

## git fetch  [origin] [branch]  

Fetch all branches from [origin], along with all required commits and files. Specifying a branch only fetches from that branch.  

## git merge [branch]  

This merges the specified branch [branch] into the branch you're on.  

## git pull [origin] [branch]  

Rolls **fetch** and **merge** into one command - fetch the remote copy of the specified branch and merge it into the local copy.  

## git push [origin] [branch]  

Push changes to remote repo, branch [branch] - default branch is [master]  

## git diff 

See differences between files line by line  

### git diff HEAD    

See the difference between your current files and your last commit  

### git diff --staged  

See the difference between your staged files and your last commit  

## git stash  

Temporarily store changes in a "dirty" working directory  

