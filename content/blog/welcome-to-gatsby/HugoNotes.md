

# Hugo Notes

## Installation on Windows

Cmd as admin
Run cholatey  (Install Chocolatey)
 choco install hugo-extended -confirm
(​​​choco​​ ​​install​​ ​​-y​​ ​​hugo-extended  Why is this different?)

### run with a theme

To create basic web site with a theme.

git clone https://github.com/sourcethemes/academic-kickstart.git My_Website

Initialize the theme:

cd My_Website
git submodule update --init --recursive


View your new website by running the following command and then opening localhost:1313 in your web browser:

hugo server


Press Ctrl + C in the Command Prompt/Terminal

when you wish to stop viewing your local website using the Hugo server and be able to type other commands again.


SEE https://georgecushen.com/create-your-website-with-hugo/


Visual Code + HUGO + GitLab (+ Netlify  No Use Gitlab action or what ever for CI)


SEE https://gohugo.io/hosting-and-deployment/hosting-on-gitlab/

SEE https://georgecushen.com/#posts




## Build from template


hugo new site Viewtec
git init
#Theme source from https://themes.gohugo.io/

git submodule add https://github.com/gcushen/hugo-academic.git themes/academic   <--- changet this  depending on theme

echo 'theme = "ananke"' >> config.toml


## Build from scratch

​​hugo​​ ​​new​​ ​​site​​ ​​<sitename>

This creating dirs:
archetypes,content,data,layouts,static,themes
and files:
archetypes\default.md
config.toml


## Toml file
Key entries
`
baseURL = ​"http://example.org/"​
​languageCode = ​"en-us"​   should this be en-gb or what
title = ​"Brian's Portfolio"
`

## Basic home page
To start basic web page skeleton, then start extending with Hugo placeholders
Such as:
```
<!DOCTYPE html>
<html lang="en-GB">
  <head>
    <meta charset="utf-8">
    <title>{{ .Site.Title }}</title>
  </head>
  <body>

    <h1>{{ .Site.Title}}</h1>

    {{ .Content }}

  </body>
</html>

```
## HUGO notation
Site  means get data from  toml file
Content from content directory as mark down files.
dot refers to current context
Home page with Hugo is from the file named _index.md in the content directory.

## Using Archetypes

Archetype are default contents stored under the archetypes folder.
the   markdown files contains  YAML front matter
Aside  what is front matter:

## Layouts

Single page layouts  use file at layout/_default/single.html
This is probably  the about page amoungs others ????


## Hugo file structure

Meta data followed by Markdown content, Meta data is called front matter.
```
---
title:
date:
draft:
---
# Content
```
## Content blocks and partials

Hugo provides a single place for skeleton html  that all other layouts  build on. When you created the theme, it generated it for you.

Locate the file themes/basic/layouts/_default/baseof.html

The content of the file is as  follows:

```html
<!DOCTYPE html>​
​ <html>
​      {{- partial "head.html" . -}}
​     <body>
​        {{- partial "header.html" . -}}
​        <div id=​"content"​>
​          {{- block "main" . }}{{- end }}
​          </div>
​        {{- partial "footer.html" . -}}
​    </body>
​ </html>
```
The  blocks referred to as partials used for headers footers navigation etc blocks.
these are stored in the directory themes/<themename>/layouts/partials/


### CSS
 stylesheet itself stored at themes/<>themename/static/css/style.css. are are referenced in html as
 attributes. (As in Standard html5)
## Basic Theme and How to build

Basic Hugo theme is made from these files:
```
​ 	layouts
​ 	├── _default
​ 	│   ├── list.html
​ 	│   └── single.html
​ 	└─── index.html
```
To create a theme:

* ​​hugo​​ ​​new​​ ​​theme​​ <​​themename>
* Move your existing layout files into this new theme. Move the layouts/index.html file to themes/<themename>/layouts/index.html, and then move layouts/_default/single.html to themes/<themename>/layouts/_default/single.html.


 * Add a reference the theme in the config.toml file

`
 theme="basic"
`
run command
> hugo server

## Add Content to sections


## Site deployment from public folder



## testing local server
-------------------

hugo server

 localhost:1313

## Commands Crib list

Check version:  ​​hugo​​ ​​version
Help: Hugo help
Build and deploy site in memory: ​​hugo​​ ​​server
(Visit http://localhost:1313 in your web browser to see your home page, ctrl C to stop hugo server)

Output Hugo website to disk: hugo (This generates site in public directory)
Cleaning public folder: hugo​​ ​​--cleanDestinationDir or  (rm - public && hugo is this bash?)
Create a new Markdown file:  ​​hugo​​ ​​new​​ ​​about.md
minefy files: ​​hugo​​ ​​--cleanDestinationDir​​ ​​--minify  (something mot clear here with delted files and new content remove directory)

## Resources

https://brew.sh

[8]
https://chocolatey.org

[9]
https://docs.brew.sh/Homebrew-on-Linux

[10]
https://github.com/gohugoio/hugo/releases

[11]
https://github.com/toml-lang/toml

[12]
https://golang.org/pkg/text/template/

https://www.w3.org/TR/css-flexbox-1/

[14]
https://getbootstrap.com/docs/4.1/getting-started/introduction/

[15]
https://themes.gohugo.io/
