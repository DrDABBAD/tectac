---
title: Git Recipes
date: 2021-09-12 00:00:00 +0300
description: # Add post description (optional)
img: ./software.jpg # Add image post (optional)
tags: [git Cheatsheet, git] # add tag
---

Git Crib Notes

## General things to know

Workflow of git:

* Workingspace: holds the actual files this is what you see and edit.
* Index: Acts as a staging area. That is, snapshot for next commit. Will be done by git add command.
* HEAD : Points to the last commit (and current branch) you've made.

Git has three stages:

* Committed : means data is safely stored in your local git repository.
* Modified : means you've changed the file but not committed.
* Staged : means you've marked a modified file in its current version to go into your next commit snapshot.

## initialize new git repository on gitlab

Notes on setting a gitlab repository from your local  machine.

### Create

`
git init
`

### add  directory to exclude  in gitignore

In this case /public directory to our .gitignore file when using hugo

`
echo "/public" >> .gitignore
`

### commit and push code to main branch

`git add .
git commit -m "Initial commit"
git remote add origin https://gitlab.com/YourUsername/your-hugo-site.git
git push -u origin main`

## rename master to main

git checkout master # switch to master if needed
git branch -m master main
git status
if using github via web browser resolve any setting for default branch and protected status
then
git push -u origin main
git push origin --delete master

if you have a local master and the remote is already main

```CLI
# Switch to the "master" branch:
$ git checkout master

# Rename it to "main":
$ git branch -m master main

# Get the latest commits (and branches!) from the remote:
$ git fetch

# Remove the existing tracking connection with "origin/master":
$ git branch --unset-upstream

# Create a new tracking connection with the new "origin/main" branch:
$ git branch -u origin/main
```

Check any CI tools for issues
Check documentation  for main

## working with remote repositories

```git
git remote -v  # show URL of remote repository

git remote add <shortname> <url> # Creates a new connection or alias to a remote repository.
git remote  remove <shortname> # removes alias
```

*example*
`
git remote add production https://xxxx@github.com/xxxx/example.git
`

## Compare local and (or) remote

```git
git status
git status -v
git status -v -v
```
git status tells you what you staged but not committed and what you have modified in the workspace but not staged. Basically staged is a checkpoint

To see the difference between staged and unstaged use:
`git diff
`

To see whats change  in workspace since the last commit
git diff HEAD

To see the difference between HEAD the repository and staged
git diff --staged

Does this mean you can have and see multiple check points?

### Other ways of comparing files

```git
git log <main> <feature-branch>  # compare local and feature
git log <origin/main> <main>     # compare remote and local
```

NOT SURE THIS RIGHT
First list all branches.

git branch -a

git diff \<local branch\> \<remote\>/\<remote branch>
git diff --stat --color remotes/main/master..origin/master
git diff remotes/main/master..origin/master

For example

 git diff main origin/main

## comparing the upstream branch

 git diff @{upstream}
If you want to compare your current HEAD with the upstream branch (thanks @Arijoon):

git diff @ @{upstream}

## Adding committing and the git index


The git add command adds content from the working directory into the staging area (or"index") for the next commit.

```git
git add
git add fileName
git add -A        #add all
git add . # all current directory
git add -u # update all tracked files
```

The git commit command takes all the file contents that have been staged with git add and records a new permanant snapshot in the database and then moves the branch pointer on the current branch up to it.

```git
git commit -m ""
git commit -a -m "by pass staging and use of add "
```

But use with caution as it does not give very trackable commits.

What can you do with the index staged files?

## Pull or fetch

Pull can be though as fetch  then merge most of the time. Thus fetch if you want the local changes avaialbe but not in your  workspace.



## Merge and rebase

Things to know about merge and rebase (and what about checkout)

Whats the difference

Why don't you use checkout

From git version 2.23 produced two commands there

switch
restore

Basically if you checkout a file you you revert or reverse the modification of an unstaged file.

When not to rebase

### Merging branches

```git
 git switch <branch>
 git merge <feature-branch>
 ```

 #### Safe remote merge steps

 1. git fetch origin
 2. git log --oneline main..origin/main
 3. git checkout main
 4. git log origin/main
 5. git merge origin/main

 #### But how do you revert

### Rebase branches

```git
 git switch <branch>
 git rebase <feature-branch>
 ```

## When to use  git stash

To "Stash the changes in a dirty working directory away".

* CASE 1: You are in the middle of something, and you have got a call to urgently resolve a bug.
* CASE 2: You have uncommitted files and try to “git pull” and due to conflicts

Commands to use:

```git
git stash push -m <name or message> # put stash on a stack
 git stash push -m <message> <path-of-file> #stash a named file
git stash list  # list delta on stack
git stash pop  #  applies delta to work space throws away code on  stack
git stash pop n # applies agiven delta to workspace
git stash apply – keeps it in the stash-list even after applying it, for later reuse.
```

Other commands show drop and clear

## Resources

[Gist Crib sheet](https://gist.github.com/gregrickaby/70f10dfa9385c1d5cc49f99562ffb816)
[For fast reference see:](http://gitref.org/)
[git Tips:](https://github.com/git-tips/tips)
[git workflow](https://blog.osteele.com/2008/05/my-git-workflow/)
[git index](https://newbedev.com/what-is-the-difference-between-git-diff-head-vs-git-diff-staged)
[git fetch](https://www.atlassian.com/git/tutorials/syncing/git-fetch)
[Using stash](https://bluecast.tech/blog/git-stash/)
