---
title: Javascript Articles
date: 2017-09-10 00:00:00 +0300
description: # Add post description (optional)
img: ./js-1.png # Add image post (optional)
tags: [Js, Javascript] # add tag
---


## Set default init properties

```js
npm config set init.author.name  "David"
npm config set init.author.email "David.myname@gmail.com"
npm config set init.author.url   "davidMyname.com"
npm config set init.license      "MIT"

```
To check that these properties were added correctly, type

npm config edit
or
npm config edit -g  for  global settings

To go back to the default settings, you can use the following script.



## Tips

console.table() can be used to log any object or array in table form.

## Resources

Useful links of stuff to read:

[mongoDB](../javascript/mongodbshell)
[Embedded languages in JS](https://github.com/viebel/klipse)
