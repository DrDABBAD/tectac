---
title: Check list for Hugo website
date: 2021-09-12 00:00:00 +0300
description: # Add post description (optional)
img: ./software.jpg # Add image post (optional)
tags: [Hugo, static website] # add tag
---

## Check list of things to check for a hugo website

Brief check list of config items to check to ensure website renders correctly.

## Meta tags

Globally defined in the file:

## Global tags and descriptions
### Og:description  defined where ???
### og:image
In Hugo defined in config.toml or params.toml as  [homepage_meta_tags] rendered from  layout file index.html
The URL of an image for the social snippet.
e.g (TO BE REPLACED) https://pjgcreations.co.uk/wp-content/uploads/2017/07/PJGCreationLogo4-e1382782436397.jpg

"Note that this is perhaps the most essential Open Graph tag because it occupies the most social feed real estate", Ist image that appears when you post website or video content to your social accounts. used in [twitter cards](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started)  https://smallseotools.com/open-graph/




Syntax
<meta property="og:image" content="https://ahrefs.com/blog/wp-content/uploads/2020/01/fb-open-graph-1.jpg" />
Best practices
Use custom images for "shareable" pages (e.g., homepage, articles, etc.)
Use your logo or any other branded image for the rest of your pages.
Use images with a 1.91:1 ratio and minimum recommended dimensions of 1200x630 for optimal clarity across all devices.

Checking image tools:  smallseotools.com and use the OG checker tool

## Robots.txt

Expect Robots.txt hugo site location as template either:

/layouts/robots.txt
/themes/<THEME>/layouts/robots.txt

```
User-agent: *
{{ range .Pages }}
Disallow: {{ .RelPermalink }}
{{ end }}
```

Aside: Hugo tags used for robots.txt

\{\{ rage page\}\}  : means


or as static file  in the static directory.

Check Not
Disallow: /

Also check config.yaml files for enableRobotsTXT true when using template otherwise false.

### URLS and URL paths

problem: path built with url as part of path on CI site.

### Images and Graphics

Favicon Expect root directory, Link generated  ,config page
### About us

### Services


### contact us

### Blog content

### Analytics and crawling

### Trouble shooting


[TOCSS … this feature is not available in your current Hugo version](https://gohugo.io/troubleshooting/faq/#i-get-this-feature-is-not-available-in-your-current-hugo-version)
Check version on local machine shows "Hugo Static Site Generator v0.62.2/extended windows/amd64 BuildDate: unknown" So Im using hugo extended locally there error is in the docker file.

Notes: on hugo extended (https://discourse.gohugo.io/t/hugo-extended-on-gitlab-pages/21986)


## Resources

[Metatags](https://ahrefs.com/blog/open-graph-meta-tags/#which-open-graph-tags-to-use)
