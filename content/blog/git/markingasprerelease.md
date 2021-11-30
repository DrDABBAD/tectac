## Marking as pre-release
A nice little decorative feature is that you can mark a release as a prerelease,
 meaning you can inform the users that it's not ready for production
  but that they can still download and test it. Let's make a
  prerelease of the develop branch, which contains new commits that do not exist in master yet:
```
git checkout master
git checkout -b develop
echo "0.6rc1" > version.txt
git add version.txt
git commit -m "0.6 pre-release"
git push origin developMarking as pre-release
```


## Git Push

git push only updates the corresponding branch on the remote

### *Common Usage*

* git push -f: Force a push that would otherwise be blocked, usually because it will delete or overwrite existing commits (Use with caution!)
* git push -u origin [branch]: Useful when pushing a new branch, this creates an upstream tracking branch with a lasting relationship to your local branch
* git push --all: Push all branches
* git push --tags: Publish tags that aren't yet in the remote repository

git status shows which branch on.


## Fixing  and understanding



### Accidentally committed to the wrong branch

Checkout to the branch that you intended to commit to: git checkout [branchname]

Merge the commits from the branch that you did accidentally commit to: git merge [master]
Push your changes to the remote: git push

Fix the other branch by checking out to that branch, finding what commit it should be pointed to, and using git reset --hard to correct the branch pointer



###  What's git reset hard and soft

To understand need to understand the areas of git

Working directory | To see dir, ls
---------------------------------
                  | Bring inline with Stage
                  | remove untracked files git clean (with option)
-------------------------------------------
Staging index:    |
                  |To See git ls-files -s
                  |Bring inline with working git add
commit history    |
                  | To See git log
                  | Undo comits git revert but no by moving the commit pointer back




But what does git reset do?

git reset will move the HEAD ref pointer and the current branch ref pointer

And what are the command line arguments --soft, --mixed, and --hard ?

They direct how to modify the Staging Index, and Working Directory trees.

-- hard means reset both stage and working directory to the specified commit.

--- mixed  "The ref pointers are updated. The Staging Index is reset to the state of the specified commit. Any changes that have been undone from the Staging Index are moved to the Working Directory".
--- soft

### fixing the remote branch