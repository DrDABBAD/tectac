

# React

## Dev tools

see (https://github.com/facebook/react-devtools) mae sure you are the v3 (15/10/2021) branch
find pre packed links for extensions represent the current stable release.

Chrome extension
Firefox extension
Standalone app (Safari, React Native, etc)

Page with react components will show the  react logo un-greyed (weird molecule thing).

### Install Node

Check for installation
node -v
if missing
[goto node.js website] (http://nodejs.org/) and install
node and npm the node package manager.


## Starting a project

The key commands are:

``` npm
npm init -y

npm install package-name

npm remove package-name
```

Alternatively use yarn

Install yarn globally
```yarn
npm install -g yarn


Is there no yarn init package ?
To install  and remove package

yarn add package-name

yarn remove package-name
```

finally to run yor project

npm run start

## git and git hub tasks

* Create a new repository on GitHub.

Open your terminal.

* Initialize the local directory as a Git repository:

git init    WHAT ABOUT MAIN

* Add the files to your new local repository:

git add .

* Commit the files that you’ve staged in your local repository:

git commit -m "initial commit"

* Copy the HTTPS URL of your newly created repo

*In the Command prompt, add the URL for the remote repository where your local repository will be pushed.

git remote add origin remote repository URL

* then remote -v

git remote -v

* Push the changes in your local repository to GitHub using the following command :

git push -f origin master

## git deployment to github pages

npm install gh-pages — save-dev

After that, go to your package.json file in your root directory

add the homepage property at the top level.

"homepage": "https://username.github.io/repository-name",

add those two lines in the scripts property:

"predeploy": "npm run build",
"deploy": "gh-pages -d build"

To deploy project

npm run deploy

## Core javascript needed for react

### const and variables

````js
const pizza = true;  # cant be overrwritten
var pizza2 = true;
pizza2 = false;  # ehere as variables can
```

##  Lexical variable scope

What is lexical scope

var and let are used to set variables.  (In old javascript only var )

```js
var topic = "JavaScript";

if (topic) {
  let topic = "React";
  console.log("block", topic); // React
}

console.log("global", topic); // JavaScript
with let the value of topic is not reset outside of the block. this is not the case if var is substituted for the above code. var  from  inside the curly braket will reset the global value of topic
```
This is the same for  loop counters
with for loops

## concatenation

Traditional string concatenation uses plus signs to compose a string using variable values and strings:
```
console.log(lastName + ", " + firstName + " " + middleName);
```
With a template, we can create one string and insert the variable values by surrounding them with ${ }:
```
console.log(`${lastName}, ${firstName} ${middleName}`);
```
Templates are better because the honour white space


### Function Declarations

'''js
 ** Declare
function logC() {
  console.log("wonderful!");
}
** Invoke
logC();
'''

### Function Expressions
 This just involves creating the function as a variable:

const logC = function() {
  console.log("Awful");
};

logC();
'''

Function declarations are hoisted and function expressions are not.

**What does hoisting mean ?**
Hoisting is JavaScript's default behaviour of moving declarations to the top whether they are variables or function expressions.
You can invoke a function before you write a function declaration. You cannot invoke a function created by a function expression.

### Arrow functions in javascript

## resources

learning-reat(https://github.com/moonhighway/learning-react)