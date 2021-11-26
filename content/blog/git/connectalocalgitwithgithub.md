---
title: git with git hub
date: 2021-09-12 00:00:00 +0300
description: How to setup a connection between git and git hub # Add post description (optional)
img: ./software.jpg # Add image post (optional)
tags: [git, github] # add tag
---


## Connect it to github

You’ve  got a local git repository. but how does it connect to github.
Generally the instruction are start a new project github then clone to your local machine In fact there is no need to connect to github at allif you dont want to share code.

 If you to share coed via  github, do the following:

Go to github and create a empty   repository.
1. Log in to your account.
2. Click the new repository button in the top-right..
3. Click the "Create repository" button.




Now, follow the second set of instructions, "Push an existing repository…"

$ git remote add origin git@github.com:\<username\>/\<new_repo\>

or

$ git remote add origin https://github.com/\<username\>/\<new_repo\>

if you don't use SSH connections.
$ git push -u origin main

There are still some bits missing on this.
Passwords, accessibility setup SSH keys.
