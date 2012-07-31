---
layout: post
title: 12 Factor Awesomeness for Django apps
snip: The perfect 12 Factor app is an elusive mistress to most of us.  Here is my take on making it come a bit closer to reality.
---

{{ page.title }}
===

The [12Factor][1] app is a collection of design principles, laid down by the good people at Heroku, that help in producing web applications that are easily scalable across Cloud PaaS providers and also tailored to suit developers needs.

I spent quite a lot of time this past week working out methods to ensure all the factors were met.  Here, I share my solutions, using django and python, to the guidelines posed by the 12Factor method.


## 1. Codebase

*One codebase tracked in revision control, many deploys*

I am used to the [git-flow][2] branching model and it seems that git-flow can easily handle 12Factorness.  There are two branches with an infinite lifetime.  By convention, name them 'master' and 'develop'.  At any time, 'master' reflects the current state of production and 'develop' is deployed on staging.  

Staging is our main repo, probably on /staging/\<app_name\> or something similar.  This is the repo that developers clone when they want to work on the app.  It contains both the main branches.  The repo contains a git-hook that checksout the latest commit on the 'develop' branch when a git push is done to it.

Production is a second repo that contains only the master branch and is used only for pushing releases out to end users.  It contains a hook similar to the staging repo.  The only difference being that the 'master' branch is checkedout on a git-push.  Production is on /production/\<app_name\> or something similar.


## 2. Dependencies

*Explicitly declare and isolate dependencies*

This is a tricky bit.  Especially if you want to make the bootstrapping process extremely simple for the new developer.  I would actually love something like a single bootstrap script that sets up a cute little virtualenv and also installs all the required libraries to this virtual env.

Here are the steps that my 'bootstrap' script now needs to execute in order:

- Setup a virtualenv
- Activate the above virtualenv
- Install the dependencies for the app, as declared in the requirements.txt file to the virtualenv

[1]: http://www.12factor.net/
[2]: http://nvie.com/posts/a-successful-git-branching-model/
