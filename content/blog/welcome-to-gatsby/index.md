---
title: 'Welcome to Gatsby!'
date: 2021-04-06 13:32:20 +0300
description: Notes on Using Gatsby. # Add post description (optional)
img:  ./software.jpg# Add image post (optional)
---

## What is Gatsby

Gatsby is a free and open source framework based on React.
But what does it do?
Creates web sites and apps, oh!.



## How does it work

## Project structure

## Project structure
```
|-- /.cache
|-- /plugins
|-- /public
|-- /src
    |-- /pages
    |-- /templates
    |-- html.js
|-- /static
|-- gatsby-config.js  //configure options for a Gatsby site, with metadata for project title, description, plugins, etc.
|-- gatsby-node.js    //implement Gatsby’s Node.js APIs to customize and extend default settings affecting the build process
|-- gatsby-ssr.js     // customize and extend default settings affecting the browser, using Gatsby’s browser APIs
|-- gatsby-browser.js  // use Gatsby’s server-side rendering APIs to customize default settings affecting server-side rendering
```

## Initial build of a site

$ gatsby new my-great-gatsby-site \
  https://github.com/gatsbyjs/gatsby-starter-blog

  other starter sites are available [see starer] (https://www.gatsbyjs.com/starters)

## modify starters

### gatsby-config.js File


### pages and components

Pages are the higher-level components used to build a site, while components can be nested within both pages and components.

file location for pages src/pages/*.js

## Basic Gatsby Usage

The most common way to generate local content:

 run `gatsby develop`, this launches a web server and auto-regenerates your site when a file is updated.

to **Creating a production build**

```gatsby
gatsby build
gatsby serve
```
There are option flags available with the above commands

The production build  outputs the built static files into the public directory.
Is there a clean up Command ?
yes
 gatsby clean

if package.json is configured for scripts
you may be able to run instead.
```
$ npm run develop
```


### lighthouse audit

Open the site in Chrome (if you didn’t already do so) and then open up the Chrome DevTools. (Lighthouse is also available for Firefox from Firefox Add-ons. )

Click on the “Audits” tab, this may be a “Lighthouse” tab depending on which version you are using. You should see a screen that looks like:

## Adding content

To add new posts, simply add a file in the `content/blog` directory.

### What is frontmatter

YAML (YAML Ain’t Markup Language) content at head of md files between triple dashed lines.
where YAML is yet another serialization standard ,think JSON. In Gatsby this parsed by the plugin gray-matter.

What does this do?

converts  md file into an object (graphql object) ?


###  Graphql

### HTML Page meta data

This is important for page ranking and seo

use to build seo.js component
This is controlled by the react helmet plugin.
See [helmet docs](https://github.com/nfl/react-helmet#example)
1. Install
2. configure
3. Use
### Markdown and Gatsby

There's support for code snippets:

```javascript
console.log('Hello, World!')
```

And also LaTeX functions using the [KaTeX plugin][katex-plugin]: $a^2 + b^2 = c^2$

You can even [link files for download](Gatsby.pdf)

Check out the [Gatsby docs][gatsby-docs] for more info on how to get the most out of Gatsby.

## gatsby repl

`
gatsby repl
`

Is used to open a Node.js read–eval–print loop (REPL)

## Integration with Strapi

Strapi is powered using Node.js and delivers your content with GraphQL.

## Gatsby with Github

Use two branches source and main
Source is used only Github pages
Main is used to track source code

So need two repositories on github
one for the pages
one for the source control

## Page deployment script

"npm run deploy all contents of the public folder will be moved to your repository’s gh-pages branch. Make sure that your repository’s settings has the gh-pages branch set as the source to deploy from."

What does tihs mean


###  Using custom domains

Create a CNAME file in the static directory.


## GraphicQL


SEE [Query with graphiQL](https://www.gatsbyjs.com/docs/how-to/querying-data/running-queries-with-graphiql/)
## Gatsby Resources

[gatsby-docs]: https://www.gatsbyjs.org/docs/
[katex-plugin]: https://www.gatsbyjs.org/packages/gatsby-remark-katex/
[strapi integration](https://strapi.io/integrations/gatsby-cms)
[Gatsby on windows] (https://docs.microsoft.com/en-us/windows/dev-environment/javascript/gatsby-on-wsl)
### gatsby with docker local

(https://augustin-riedinger.fr/en/resources/using-docker-as-a-development-environment-part-1/)   #2017


(https://github.com/DeveloperDavo/docker-node)

(https://github.com/DeveloperDavo/docker-nginx)
(https://blog.atulr.com/docker-local-environment/)
(https://www.stoutlabs.com/blog/2019-02-05-my-docker-setup-gatsby-next/)

(https://learnitmyway.com/learn-ds-algorithms/)

###  Volume and mount example

https://4sysops.com/archives/introduction-to-docker-bind-mounts-and-volumes/


## React resources

(https://learnitmyway.com/learn-react-with-these-resources/)
(https://learnitmyway.com/learn-javascript-with-these-resources/)

## Wireframe in gatsby

## Gatsby deployment pages

npm run gitdeploy (deploy)

(https://joolfe.github.io/gatsby-for-docs/03-new-project)
