
# Git Tutorial

The aim of this tutorial is to hopefully convince you of the utility of Git and to give you enough detail to get you up and running. This is NOT a definitive guide and it will not make you an expert, but there are plenty of more documentation and in depth guides available online.

N.B I have almost exclusively used Git on linux or Mac OS. The current guide should be relevant for Windows users as well if using Git bash.

# What is Git and why should you use it?

Git is a popular open-source version control system among developers. Originally, it was designed for collaborative projects between developers. Git is mostly used to store content and code in repositories. The system also provides an environment where the code can be changed, with the revisions saved for future use. The repositories are stored in a remote server but are locally saved in every team member’s computers.

Some of the benefits of using Git are:

- Open-source and widely used – it’s free to use and many resources are available online to learn the best Git practices.

- Fast and lightweight – the core part of Git and most of its operations are written and performed locally, making it faster than the centralized version control system.

- Safer backup – Git creates multiple copies of your data as it mirrors the repository to all clients, allowing more backups. Furthermore, Git can take snapshots, which are the representations of a file system, enabling you to roll back to the state when the snapshot was taken. This can be a helpful recovery solution in case of failure. (I was able to rebuild my entire thesis when my laptop failed because I used Git, GitLab,  Latex and BibTex)

- Easier Collaboration - Multiple people can work on Git repos at the same time as all the data is stored locally and then the work can be merged together (This can be tricky and requires the collaborators to have a system in place for merging code from branches).

- Great for working on multiple machines - I often use git to write code to run on the Cluster on my own machine, I can then push the changes to the repo and run thr code and then pull any output files I want back on my local machine. All of this is version controlled and tracked so If I make a mistake I can roll it back and it disappears.

- Reproducibility - code can be shared with others to allow your analysis to be reproduced by others.

# Command Line or GUI?

Git can be used in a variety of ways, the most basic and universal is by using the command line, which is what this tutorial will focus on. However, there are numerous GUI options for using Git. Most IDEs such as RStudio and Visual Studio Code have Git support built in and there are various other Git GUIs such as GutHub's GUI, SourceTree and Git Kraken.  

# Installation and configuration

## Linux

If not already installed Git can be installed via your package manager of choice (There are far to many flavours of package manager to cover all of them here and If you are using linux I assume you know how to install packages or are familiar with googling the answers).

## Mac OS

In the terminal run:

```bash
git --version 
```

If Git is installed you will get an output like this.

```text
git version 2.32.1 (Apple Git-133)
```

If it isn't installed you will get a prompt to install the command line developer tools via xcode.

## Windows

Download and install Git for Windows <https://gitforwindows.org/>

## Configuration (All OS)

Once git is installed run the following commands replacing the generic username and email with your own. These details will appear with all your commits going forward.

```bash
git config --global user.name "myusername"
git config --global user.email "example@mysite.com"
```

# Getting started with using Git on your local machine

So to set up a repository first you need to be in the directory you wish to use, in this instance we will create a new one but this will work with existing directories.

```bash
mkdir git-tutorial
cd git-tutorial
git init
```

## git status

To check the status of your repository you can run the command `git status` and you will get an output like this:

```text
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

So let's add some files and re run status:

```bash
echo "foo" > foo.txt
echo "bar" > bar.txt
git status
```

Output:

```text
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        bar.txt
        foo.txt

nothing added to commit but untracked files present (use "git add" to track)
```

So we no we are on the branch called master (This is the default branch), there are no commits yet and we now have two untracked files. In the next step we will look at how to add these files.  

## git add

The next step is to add some files to the staging area. Files in git can exist in three areas the working area, the staging area and the repository. Files in the working area can be modified and the changes will remain on the local machine until you add them to the staging area with `git add`.

```bash
# Individual files can be added to the staging area.
git add foo.txt bat.txt
# All the all the unstaged files in a directory
git add . 
# Wildcards also work
git add *.txt
```

Now lets re run the `git status` command.

```text
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   bar.txt
        new file:   foo.txt

```

## git commit

The git commit command creates a snapshot of your repository’s content at a specific time. It records the changes made to the files in your repository. On top of that, commits serve as the comprehensive project record, showing you how it has evolved. Each commit has a unique commit ID for easier reference. A commit ID is also helpful for referring to a specific commit when you need to undo a change. This command is the second step in saving the changes made to a repository. The process starts with the `git add` command for staging any new changes you want to include in a commit. Then, git commit creates a commit with those changes to a repository. The `git add` command won’t affect anything until you execute `git commit`.

```bash
# Running git commit will drop you into your default text editor so you can add a message. 
git commit 
# Commit with a message use the -m flag 
git commit -m "add in foo.txt and bar.txt"  
# Commit all tracked files (Tracked files are ones which have been added to the index using git Add at some point but may have not been staged)
git commit -a 
# commit all with a message 
git commit -am "add in foo.txt and bar.txt
```

Which ever one of these you run you should get a message similar to one below.

```text
[master (root-commit) 1398a2a] add in foo.txt and bar.txt
 2 files changed, 2 insertions(+)
 create mode 100644 bar.txt
 create mode 100644 foo.txt
```

Let's run `git status` again:

```text
On branch master
nothing to commit, working tree clean
```

So now we have created our first commit!

## git log

The git log command shows the commit history of a repository. If we run it we should get an output a bit like this:

```text
commit 7c00ad60d31a00d6027d07c51d7ed160c340ec7b
Author: David Smith <smithd@well.ox.ac.uk>
Date:   Tue Jun 14 15:08:23 2022 +0100

    add in foo.txt and bar.txt
```

## git tag

`git tag` can be used to show a key point in the repo history such as a V1.0 release or maybe the addition of an additional data set or something, this can make it easier to identify key commits if there are lots in a repo.

## git branch

`git branch` can be used to create, rename and delete other branches. 

```bash
# create new branch called foobar2.0
git branch foobar2.0 
# rename the current branch foobarMain
git branch -m foobarMain
# delete the foobarMain branch
git branch -d foobarMain
# list the branches in the repo
git branch 
# or
git branch --list
```

## git checkout

Now we have created a new branch we have to switch to it before we can start working in it. We can do this with `git checkout`.

```bash
# switch to the foobar2.0 branch
git checkout foobar2.0
# show the current branch
git branch --show-current
```

Now lets make some changes.

```bash
echo "foobarfoobar" > foo.txt

git add

git commit -m "adding in foobarfoobar"
```

## git merge

`git merge` can be used to merge your changes from a branch into another branch. So whilst in the main branch you can merge it with another branch using 'git merge'

```bash
git checkout foobarMain
git merge foobar2.0
```

The output wil be something like this:

```text
Updating 7c00ad6..2619ffe
Fast-forward
 foo.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

## git restore

One of the cool things about git is rolling back changes using `git restore`

```bash
# lets remove the bar.txt file 
rm bar.txt
ls
# now lets use git to get that file back.  
git restore bar.txt
ls
```

You can also roll back by multiple commits or for whole directories etc and but I won't go into the full details you can look at the git documentation.

# Remote Git Repositories

Up until now everything we have done has been local only. One of the great strengths of Git is the ability to collaborate and host things on remote repository hosted on GitHub or BitBucket or GitLab. So lets look at how we can set up a remote repository.

So the easiest way of setting up a remote repository is to go to your Github Account and create a new repository. You can then clone this repository by copying the url and using the command 

## git clone

```bash
git clone https://github.com/dasads44/GitTutorial.git
```

## git remote

You can also add a remote repo to an existing local repo by going to the local repo and using `git remote add`.

```bash
# You need to change the name
git remote add <name> https://github.com/dasads44/GitTutorial.git
```

## git push

To push your local changes to a remote sever you use the command `git push`

```bash
git push <remote name> <branch name>
# For example, if the remote repository name is origin and the branch name is main, the syntax should look like this:
git push origin main
```

## git pull

To pull your repo from a remote sever you use the command `git push`

```bash
git pull <remote repository name>
# For example, to retrieve the content of the main branch, use this command:
git pull main

# If you want to pull code from just one specific branch, use this syntax:
git checkout <branch name>
git pull <remote name>

#If you want to work with code on a branch named demo-v1, and the remote repository name is main. The command will be as follows:
git checkout demo-v1
git pull main
```

# Documentation

Git is very powerful and It is impossible for me to go into enough details in this session. But you can find extra information online.

Official Git Documentation
<https://git-scm.com/>

Git Cheat Sheet
https://about.gitlab.com/images/press/git-cheat-sheet.pdf