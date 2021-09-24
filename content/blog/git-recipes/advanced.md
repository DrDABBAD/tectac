# GIT Recipes

Crib Notes on Git commands.

## Navigating history

git log ; git lg
git checkout ca55e77e
git checkout master
git checkout HEAD^3
git checkout “HEAD@{1 month ago}”
git checkout :/Commit message

## Branching

git checkout -b develop # creates new branch develop and does checkout of develop
git merge feature/awesomeness # merges the branch "feature/awesomeness" into the current branch

git branch -d feature/coolthing # deletes local branch "feature/coolthing"
git push origin :feature/coolthing # deletes remote branch "feature/coolthing" from the "origin" remote

## Stash

Get single file from stash…
`
git checkout stash@{0} -- _{{filename}}_
`
Stash all files including untracked files

git stash -u
## Committing
Add specific lines of a file to the commit interactively


git add -p --
git add -p filename
Commit the staged changes

git commit -m "your commit message"
## Bisect
Trace buggy commit with git bisect…

## Manual methods

git bisect reset # only needed after a bisect
git bisect start
git bisect good <revision>

git bisect bad <revision>

# git will checkout the next revision to check
git bisect (good | bad)
## Automated methods

git bisect start
git bisect good <revision>
git bisect bad <revision>
git bisect run/path/to/decision/script args...
filter-branch
fix committer/author
##
#!/bin/sh

git filter-branch -f --env-filter'

n=$GIT_AUTHOR_NAME
m=$GIT_AUTHOR_EMAIL

case ${GIT_AUTHOR_NAME} in
     "Marco Franssen") n="Marco Franssen" ; m="marco.franssen@gmail.com" ;;
     "Marco Franssen marco.franssen@gmail.com") n="Marco Franssen" ; m="marco.franssen@gmail.com" ;;
esac

export GIT_AUTHOR_NAME="$n"
export GIT_AUTHOR_EMAIL="$m"
export GIT_COMMITTER_NAME="$n"
export GIT_COMMITTER_EMAIL="$m"
' HEAD
Remove filter-branch backup
1
git update-ref -d refs/original/refs/heads/master
Git config
[alias]
    bw = blame -w -M
    c = commit
    cc = commit --all --amend --no-edit
    ca = commit --all
    co = checkout
    cb = "!f() { git checkout `git log --until=\"$*\" -1 --format=%h`; } ; f"
    s = status --short
    d = diff
    dc = diff --cached --word-diff=color
    dw = diff --word-diff=color
    l = log
    a = add
    af = add -f
    p = push
    ss = show -1 --format="%B" --stat
    sw = show -1 --format="%B" --stat --word-diff=color
    whatis = show -s --pretty='tformat:%h (%s, %ad)' --date=short
    lg = log --graph --pretty=format:'%Cred%h%Creset %C(yellow)%an%d%Creset %s [%N] %Cgreen(%ar)%Creset' --date=relative
    lgd = log --graph --pretty=format:'%Cred%h%Creset %C(yellow)%an%d%Creset %s [%N] %Cgreen(%ar)%Creset' --date=default
    lgm = log --graph --pretty=format:'%Cred%h%Creset %C(yellow)%an%d%Creset %s [%N] %Cgreen(%ar)%Creset' --date=relative --author="marco.franssen@email.com"
    abbr = "!sh -c 'git rev-list --all | grep ^$1 | while read commit; do git --no-pager log -n1 --pretty=format:\"%H %ci %an %s%n\" $commit; done' -"

[web]
    browser = chromium-browser

[color]
    ui = always

[core]
    autocrlf = input
    pager = less -x1,5
    fileMode = false

[push]
    default = simple

[branch]
    autosetuprebase = remote
Cloning
1
git clone git@github.com:marcofranssen/grunt-dotnet-codecoverage.git
Get all remote branches as local tracking branches except master and HEAD since you already got those with the clone command.

1
for branch in 'git branch -a | grep remotes/origin | grep -v HEAD | grep -v master'; do git branch --track ${branch##remotes/origin/} $branch; done
Most probably you also want to fetch and pull the remote tracking branches


git fetch --all
git pull --all
Recovering your local branch from a force push
This will remove all commits previously on master and all commits done by yourself which are not yet pushed.


git fetch
git reset origin/master --hard
To preserve your own changes and commit them again do the following.


git fetch
git reset origin/master --soft
This will move all changes to your working directory, so you can commit them again manually.
You can also do an interactive rebase. In this case you have to pick the commits you want to keep.


git fetch
git rebase -i origin/master
Please note if you keep one of the commits you kept behind was one of the commits removed with the force push, that commit will again be reintroduced at the remote.