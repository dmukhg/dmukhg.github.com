---
layout: post
title: Building a fear-free software engineering team, Part I
snip: Creating an environment of confidence leads to faster development cycles and lesser customers being affected by bugs.
humanDate: October, 2015
cover: https://drscdn.500px.org/photo/223296927/m%3D900/v2?webp=true&sig=1957a60835e961f4ad84e47f27d3fae86cbc64ad9274a75df87ff6c0057c6394
coverAttrib: https://500px.com/photo/223296927/jump-by-kaarel-antonov
---
I started working with [TypesetIO](https://typeset.io/) a few weeks ago. We are working on a way to create research papers that let you focus totally on the content while leaving the formatting to us. In my first few weeks, I wanted to setup some basic tools that make us developers more efficient.

We are an early stage startup. Being able to make changes as fast as possible is what would keep us afloat.

I happened to come across this [beautifully written piece](https://medium.com/javascript-scene/how-to-build-a-high-velocity-development-team-4b2360d34021) on [javascript-scene](https://medium.com/javascript-scene). It describes how agility or high velocity can be achieved by eliminating fear of change in the development team. My attempts and the title of this post are inspired from the same.

We automate because we want to remove the fear of missing out on a crucial step. We write scripts and tools because we want to eliminate the fear of spending a lot of time in doing things when we are pressed for time. I think the engineering of tools and automation is really about ensuring you can get the right answers with minimal effort and without unwittingly affecting anyone.

Some of the tools we worked on are described below.

## Server names
We are targeting AWS as a deployment platform. All our servers have IP addresses. IP addresses are difficult to remember for uses like ssh or browsing. Usually, one keeps a lookup table or sets up a DNS server.

We tried setting up a DNS server, but what if that server went down? A manual lookup table is easy to access offline, but hard to keep updated and would also require you to lookup IP addresses before entering it into the browser or terminal.

To address this, we created a configuration file tracked in git that maintained a map from our given server name to its current IP address. We also have a small [script](https://gist.github.com/schatten/e3bfc70743d2da5a6596) that uses this map to modify the `/etc/hosts` file on Unix like OSes. All you have to do is clone this repo and run a script once in a while or every time there is an update. This script will pull the latest configuration from your github or somebody’s git repo and update `/etc/hosts`. This let’s you have tab-completion on the command line and memorable names for your servers.

Now when you add a new node on AWS, or re-create an old one, you change the config file accordingly and check it in. Everyone has access to these servers.

## Continuous Testing / Deployments
So far, unit test were executed only on people’s development environments. This is likely something you may forget. While you may add a git hook to ensure every commit passes unit tests, this will make you slower which is not what we want. We set up a Jenkins server and added a few hooks to our GitHub and had Jenkins run tests for all our code repositories every time there was a push to master.

I believe you should solve for the norm and not for the exceptions. The githook approach would have prevented broken builds completely. The continuous integration / testing approach may get you occasionally broken builds but our developers don’t break builds often. We did not want them to be slowed down because of something so rare.

Once a commit has all the tests passing successfully, we consider it to be a certified build. This certified build now will be deployed to our stage servers automatically by a Jenkins hook. With continuous testing and deployments, I wanted to get to a point where deployments are so natural that the master branch is considered to be sacrosanct, yet very easy to push to.

Stage is where verification of features happen within our closed group before we would ship it to production.

***

My goal with these small wins is to create a development environment and process where the amount of code that hasn’t seen production is minimal and the angst or inertia against writing new features is minimal as well.

We are looking for engineers who want to change how research is done. If you are curious, self-organising and are looking for a challenge that whets your appetite for solving large problems, get in touch at ‘careers’ at `typeset.io’.

**Update:** I have published [part II](assuring-quality-without-quality-engineering-team) of Fear Free software engineering. If you enjoyed this, you may enjoy that too.