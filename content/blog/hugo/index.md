

## Aside
gatsby Draft mode

## hugo

Aside: what is toolbox ?

## Hugo site initialisation

```
mkdir  <site directory>
hugo new site . /
git init
*Set branch to main since git still uses master*
git branch --move master main
git branch --all
(git push --set-upstream origin main) may be
git add .   # or is this  * ?
git commit -m "init commit"
```
you have now have local git repository
*Now add themes*
cd themes
git submodule add <https://github.com>\<hugotheme\> (try beautiful hugo or )
git status
git add .
git commit -m ""theme added
copy  themes example site to  parent of hugo site



git commmit  -m " theme added"

*Run the site*
Hugo server

Pushing site to gitlab
git push -u git@gitlab.com:\<username\>/\<sitename.git\>

What is the branch

### Host on GitLab

Expectations: "Host a private repo of my site content, build a Hugo site when there is a commit to the master branch and deploys the static content to GitLab pages"

But how ?

Using  two Features of Gitlabs Pages and CI you

* Commit and then Push your site to GitLab.

* A CI file created as part of your source code
This should trigger the [Git CI](https://docs.gitlab.com/ee/ci/) build and deployment to [GitLab pages] (https://docs.gitlab.com/ee/user/project/pages/index.html).
There must be template for this and [there is](https://docs.gitlab.com/ee/user/project/pages/getting_started/pages_new_project_template.html).

The CI File (Aside: YAML supports single line comments \#. ):
```yaml
image: monachus/hugo
# line above specifies the docker base image to use for our pipeline
pages:
    script:
    - hugo          # Render the Hugo site
    artifacts:
        paths:
        - public    # Tell GitLab Pages to serve the public folder
    only:
    - master
```

Alternative with a test branch

```yaml
# All available Hugo versions are listed here: https://gitlab.com/pages/hugo/container_registry
image: registry.gitlab.com/pages/hugo:latest

variables:
  GIT_SUBMODULE_STRATEGY: recursive

test:
  script:
  - hugo
  rules:
    - if: $CI_COMMIT_REF_NAME != $CI_DEFAULT_BRANCH

pages:
  script:
  - hugo
  artifacts:
    paths:
    - public
  rules:
    - if: $CI_COMMIT_REF_NAME == $CI_DEFAULT_BRANCH


```

### Notes on my deployment

First attempt

https://viewtec-web.gitlab.io//Viewtecblg/  shows wen site but not css or links
so something wrong with links why?





### [Git page access]

See [git page access](https://docs.gitlab.com/ee/user/project/pages/pages_access_control.html)

Navigate to your project’s Settings > General and expand Visibility, project features, permissions.

Toggle the Pages button


### Custom domains and SSL/TLS certificates

 A GitLab Pages website  by default is served under the default Pages domain (*.gitlab.io, for GitLab.com ,https://viewtec-web.gitlab.io//Viewtecblg/).

To create custom domain name example.com or subdomain subdomain.example.com, you need to Access to your domain’s server control panel to set up DNS records:

A DNS A or CNAME record pointing your domain held on you DNS server??  (godaddy etc) to GitLab Pages server.
A DNS TXT record to verify your domain’s ownership.


Set either external_http or external_https in /etc/gitlab/gitlab.rb to the IP and port of your Pages Daemon. If you don’t have IPv6, you can omit the IPv6 address.

#### Steps to create your domain

In Gitlab:
Navigate to your project’s Setting > Pages and click + New domain (Url expected <https://gitlab.com/viewtec-web/Viewtecblg/pages>)


Domain Related


DNS Entry  | Type  |  Destination
-------------------------------------------
  _gitlab-pages-verification-code.viewtec.co.uk  |  TXT |gitlab-pages-verification-code=138f41971dcdbc4443b02e928f54b16a
@   A  35.185.44.232   ( orignal for 123 reg  94.136.40.51
The  web pages  ip address  is
https://docs.gitlab.com/ee/user/gitlab_com/


 )



## Search for your Hugo Website

There are several options to cohse from:

* hugo-elasticsearch. Generate Elasticsearch NO
* GitHub Gist for Hugo Workflow  NO
* hugo-lunr.Using lunr.js on a static site, Hugo-lunr will create an index file of any html and markdown documents in your Hugo project.
* hugo-search-index. A library containing Gulp tasks and a prebuilt browser script that implements search.

Based on quick review hugo-lunr which is open source suites my needs.

### Using and installing lunr.js

get Js from https://github.com/olivernn/lunr.js
What about CDN method and why is is network heavy ?

### Javascript and hugo cookies

FYI
// Safe: This cookie is only visible to example.gitlab.io
document.cookie = "key=value";

// Unsafe: This cookie is visible to example.gitlab.io and its subdomains,
// regardless of the presence of the leading dot.
document.cookie = "key=value;domain=.example.gitlab.io";
document.cookie = "key=value;domain=example.gitlab.io";

O.k. I need to read up on this


## Resources

[hugo-site-on-gitlab](https://www.bryanklein.com/blog/hugo-site-on-gitlab/)
(https://docs.gitlab.com/ee/user/project/pages)

(https://gohugo.io/getting-started/quick-start)

(https://blog.adrianistan.eu/2016/05/26/tutorial-hugo-espanol-generador-sitios-estaticos)

https://about.gitlab.com/blog/2019/02/20/start-using-pages-quickly/
https://tkainrad.dev/posts/using-hugo-gitlab-pages-and-cloudflare-to-create-and-run-this-website/

### Resource search

### Template

[Hugo](https://pages.gitlab.io/hugo/)

[video beautiful hugo and gitlab](https://www.youtube.com/watch?v=-q6ZiCroiGM)