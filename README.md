# This is a course on how to use Git

Git is a version control system for source code.

Git thinks of its data like a set of snapshots of a mini filesystem. Every time you save the state of your project in Git), it basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot.

Here are some bonus things too:
https://www.youtube.com/watch?v=1ffBJ4sVUb4
https://learngitbranching.js.org/
http://think-like-a-git.net/


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

To create/initialise a new repository inside a new local folder. This will create a new folder **.git** in the Working Directory which houses all the information about the Repository. It will also create a **master** barnch
```
git init
```
</br>
It is good practive to have these files in the repository

`.gitignore` conatins file and folder name/prefixes/suffices for all the thing that should be ignored when commiting

`README.md` conatins the information about the repository

`master` branch is not a special branch. It's exactly like any other branch. The only reason nearly every repository has one is that the `git init` command creates it by default and most people don’t bother to change it.

If you want to get and existing repository from https://github.com/

```
git clone [repo https or ssh]
```

</br>
To check the current status of the Working Directory.

```
git status
```

</br>
To view the log of commits made. Logs contain the SHA, Authoer, Date, Message.

The `--oneline` argument display the first part of the SHA and the message only. The `--stat` argument shows extra statistics about how nay lines were changed. The `--patch` shows the actual content of the file.
```
git log
git log --oneline
git log --stat
git log --patch
git log --patch fdf5493
```

</br>

To view the latest SHA's `--patch`.

```
git show
```

</br>

To add any current changes to the Staging Index. Using `.` will stage all current changed files/folders.

```
git add [file-name]
git add [file-name] [file-name-2] [file-name-3]
git add .
```

</br>

To remove any current changes from the Staging Index. This will not delet files or folders.

```
git rm --cached
```

</br>

To commit the Staging Index. Using `-m "some message"` will add the commit message upon commit bypassing an editor. using `--ammend` will modify the last commit.

```
git commit
git commit -m "[message]"
git commit --ammend
```

</br>

To see any changes not yet commited. Actually for some reason `git diff` is the same as `git log --patch`

```
git diff
```

</br>

Tags can be used to give special meaning to a particlay commit (i.e. v1.0 of a new code base). The `-a` tells git where going to create an annotated flag. The `-d` can be used to delete a tag if it's wrong before a commit. Providing the SHA allows you to tag or remove tages from any commit.

```
git tag
git tag -a v1.0
git tag -d v1.0
git tag -a beta a87984
git tag -d beta a87984
```

</br>

To create a new working branch so you are not working on the master branch. Using `branch` alone will just show you what bracnhes there are. Providing a branch name will create a new local branch. Using `-d` will delete the branch.
```
git branch
git branch [branch-name]
git branch -d [branch-name]
```

</br>

To change the Working Directory to a new or existing branch. Providing the `-b` argument will create a new branch like in `branch` above and moves to the new branch staright away.

```
git checkout [branch-name]
git checkout -b [branch-name]
```

</br>

Combined branches together is called merging. All branches get merged into the current `CHECKED OUT` branch.

```
git merge
git merge [branch-name-to-merge-in]
```

</br>

To undo a merge on the wrong branch.

```
git reset --hard HEAD^
```

</br>

To merge an updated master into a branch. DO NOT rebase commits that exist outside your repository and that people may have based work on.

```
git checkout [branch-name-your-working-on]
git rebase master
```

</br>

Undo all changes made in a commit and make a new commit. The SHA of a specific commit can be provided.

```
git revert
git revert [SHA]
```

</br>

Erase a commit. Resting is dangerous. Using `misxec` which is the default resets changes back to the Working Directory. Using `soft` removes commit back to the Staging Index. Using `hard` throws out all changes made in the commit.

```
git reset
git reset [SHA]
git reset --mixed
git reset --soft
git reset --hard
```


# WHAT TO DO WHEN

## RESOLVING A MERGE CONFLICT

Merge Conflict Indicators Explanation

`<<<<<<< HEAD`

 Everything below this line (until the next indicator) shows you what's on the current branch.

`|||||||`

 Merged common ancestors everything below this line (until the next indicator) shows you what the original lines were

`=======`

Is the end of the original lines, everything that follows (until the next indicator) is what's on the branch that's being merged in

`>>>>>>>`

Heading-update is the ending indicator of what's on the branch that's being merged in (in this case, the heading-update branch)

</br>

To resolve a merge conflict, you need to:

1) use `git status` to check what is wrong
2) choose which line(s) to keep
3) remove all lines with indicators
4) stage, commit, then push

</br>

# FILES AND FOLDERS

## .git directory structure

![](img/gitfolder.jpg)

**Directories**

`branches:` where git keeps a record of your local branches.

`hooks:` this is where we could place client-side or server-side scripts that are invoked after the corresponding Git commands. (i.e. send an email when a commit is made).

`info:` contains the global excludes file.

`logs:` stores the changes made to refs in repository.

`objects:` this directory will store all of the commits we make.

`refs:` this directory holds pointers to commits (basically the "branches" and "tags").

</br>

**Files**

`config:` where all project specific configuration settings are stored. If you want your work email to be used for a specific project rather than your personal email, that change would be added to this file.

`description:` this file is only used by the GitWeb program. ignore it.

`HEAD:` points to the branch you currently have checked out.

`index:` where Git stores your staging area information.

`packed-refs:` consists of packed heads and tags. It is useful for an efficient repository access.

</br>

## .gitignore

blank lines can be used for spacing

`#` marks line as a comment

`*` matches 0 or more characters

`?` matches 1 character

`[abc]` matches a, b, _or_ c

`**` matches nested directories
- i.e. (a/**/z) matches (a/z, a/b/z, a/b/c/z)

</br>

# GIT Glossary

**Branch:** a new line of development is created that diverges from the main line of development.

**Checkout:** is when content in the repository has been copied to the Working Directory.

**Commit:** save the snapshot.

**HEAD:** the leading branch. Usually Master.

**Master:** the default working branch of any repository.

**Merge conflict:** will happen when the exact same line(s) are changed in separate branches.

**Origin:**

**Remote:**

**Repository:** a directory which contains your project work, as well as a few files.

**SHA (Secure Hash Algorithm):** an ID number for each commit. It is a 40-character string and calculated based on the contents of a file or directory structure in Git.

**Staging Index:** a file in the Git directory that stores information about what will go into your next commit.

**Working Directory:** the files that you see in your computer's file system.