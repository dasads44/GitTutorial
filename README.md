
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

- Great for working on multiple machines - I often use git to write code to run on the Cluster on my own machine, I can then push the changes to the repo and run thr code and then pull any output files I want back on my local machine. All of this is version controlled and tracked so If I make a mistake I can roll it back and 

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

Download and install Git for Windows <https://gitforwindows.org/>[https://gitforwindows.org/]

## Configuration (All OS)

Once git is installed run the following commands replacing the generic username and email with your own. These details will appear with all your commits going forward.

```bash
git config --global user.name "myusername"
git config --global user.email "example@mysite.com"
```

