


# Node JS Basics

 nvm-windows that offers Windows users the option of easily managing Node environments.

## NVM Installation

### uninstall any existing versions of Node.js

delete any existing Node.js installation directories
(such as C:\Program Files\nodejs)
delete the existing npm install location
(such as C:\Users\<user>\AppData\Roaming\npm)

### Windows instalation

Install from (https://github.com/coreybutler/nvm-windows/releases)


## Switching version

nvm use node ...

## lsiting installed version s
nvm ls

## Per project version

type nvm use. nvm will then read the contents of the .nvmrc file and use whatever version of Node you specify.


## Node REPL

Node’s REPL a try:

$ node
> console.log('Node is running');
Node is running


## npm package management commands


 npm list : List pacakges


 ## PRoject setup

 ```
 $ mkdir project && cd project

$ npm init
`
  npm audit  and  npm audit fix to find and fix security problems.


  ## Express Generator



  ## Database usage

  MongoDB and Robomongo

 Download [Community edition](https://fastdl.mongodb.org/windows/mongodb-windows-x86_64-5.0.5-rc0-signed.msi)


## Express generator

Install is simple just run:

```node
npm install express-generator -g
express myapp
cd myapp
npm install
npm start
```

## Express view engines which one?
- v option

## Express Application structure

app.js  containes part of app
public  holds js and ccs
routes  holds routes
views    renderes pages

### Directory stucture expected


```
  app.js
    /bin
        www
    package.json
    package-lock.json
    /node_modules
        [about 6700 subdirectories and files]
    /public
        /images
        /javascripts
        /stylesheets
            style.css
    /routes
        index.js
        users.js
    /views
        error.pug
        index.pug
        layout.pug
```

sse [skeleton_website](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/skeleton_website)