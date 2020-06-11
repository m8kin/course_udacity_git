# This is a course on how to use Git

Git is a version control system for source code.

Git thinks of its data like a set of snapshots of a mini filesystem. Every time you save the state of your project in Git), it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot.

## Download Git
https://git-scm.com/downloads


## First time git configuration

Funt the below line by line in the command line.

```
git config --global user.name [Your-Full-Name]

git config --global user.email [your-email-address]

git config --global color.ui auto

git config --global merge.conflictstyle diff3

git config --list
```

You can also set a default code editor i.e. for VSCode.
```
git config --global core.editor "code --wait"
```

# Git Code

To create/initialise a new repository inside a new local folder. This will create a new folder **.git** in the Working Directory which houses all the information about the Repository.
```
git init
```

If you want to get and existing repository from https://github.com/
```
git clone [repo https or ssh]
```

To check the current status of the Working Directory.
```
git status
```

To view the log of commits made. Logs contain the SHA, Authoer, Date, Message.

The `--oneline` argument display the first part of the SHA and the message only. The `--stat` argument shows extra statistics about how nay lines were changed. The `--patch` shows the actual content of the file (can be quite verbose so the first 7 characters of the SHA can also be provided).
```
git log
git log --oneline
git log --stat
git log --patch
git log --patch fdf5493
```

To view the latest SHA's `--patch`.
```
git show
```

To add any current changes to the Staging Index. Using `.` will stage all current changed files/folders.
```
git add [filename]
git add [filename] [filename2] [filename3]
git add .
```

To remove any current changes from the Staging Index. This will not delet files or folders.
```
git rm --cached
```

To commit the Staging Index. Using `-m "some message"` will add the commit message upon commit without opening up an editor.
```
git commit
git commit -m "[message]"
```

# .git directory structure

![](img/gitfolder.jpg)

**Directories**

`branches:` where git keeps a record of your local branches.

`hooks:` this is where we could place client-side or server-side scripts that are invoked after the corresponding Git commands. (i.e. send an email when a commit is made).

`info:` contains the global excludes file.

`logs:` stores the changes made to refs in repository.

`objects:` this directory will store all of the commits we make.

`refs:` this directory holds pointers to commits (basically the "branches" and "tags").


**Files**

`config:` where all project specific configuration settings are stored. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.

`description:` this file is only used by the GitWeb program. ignore it.

`HEAD:` points to the branch you currently have checked out.

`index:` where Git stores your staging area information.

`packed-refs:` consists of packed heads and tags. It is useful for an efficient repository access.

# GIT Glossary

**Branch:** a new line of development is created that diverges from the main line of development.

**Checkout:** is when content in the repository has been copied to the Working Directory.

**Commit:** save the snapshot.

**HEAD:**

**Master:** the default working branch of any repository.

**Origin:**

**Remote:**

**Repository:** a directory which contains your project work, as well as a few files.

**SHA (Secure Hash Algorithm):** an ID number for each commit. It is a 40-character string and calculated based on the contents of a file or directory structure in Git.

**Staging Index:** a file in the Git directory that stores information about what will go into your next commit.

**Working Directory:** the files that you see in your computer's file system.