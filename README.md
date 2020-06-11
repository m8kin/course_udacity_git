# This is a course on how to use Git

Git is a version control system for source code

Git thinks of its data like a set of snapshots of a mini filesystem. Every time you save the state of your project in Git), it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot.

## Download Git
https://git-scm.com/downloads


## First time git configuration

Funt the below line by line in the command line

```
git config --global user.name [Your-Full-Name]

git config --global user.email [your-email-address]

git config --global color.ui auto

git config --global merge.conflictstyle diff3

git config --list
```

You can also set a default code editor i.e. for VSCode
```
git config --global core.editor "code --wait"
```

## Git Code

To create/initialise a new repository inside a new folder we `git init`. This will create a new folder **.git** in the Working Directory which houses all the information about the Repository.
```
git init
```

![.git folder](img/git folder.jpg)





## GIT Glossary

**Branch:** a new line of development is created that diverges from the main line of development

**Checkout:** is when content in the repository has been copied to the Working Directory

**Commit:** save the snapshot

**Repository:** a directory which contains your project work, as well as a few files

**SHA (Secure Hash Algorithm):** an ID number for each commit. It is a 40-character string and calculated based on the contents of a file or directory structure in Git

**Staging Area:** a file in the Git directory that stores information about what will go into your next commit

**Working Directory:** the files that you see in your computer's file system

