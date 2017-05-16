---
layout: post
title: Building a fear-free software engineering team, Part II
snip: Flying solo; Assuring quality without a quality engineering team. Providing control over quality to engineers by streamlining deployment.
humanDate: November, 2015
---

At [TypesetIO](https://typeset.io/) we don’t yet have QA engineers. This doesn’t have to mean that we are not focused on quality. Quality Engineers are human and may make mistakes. The same applies for Development Engineers. If it is possible for both to make mistakes, I would rather make those mistakes cost less than trying to ensure that there are no mistakes.

Finding bugs gets tougher as less remain to be discovered. 100% quality is achievable but it comes at the cost of infinite time. You will find that the first few bugs are discovered about the same time while the last few may stay in the software for days or even years.

As a web-software org, our focus is on continuous delivery. We want minimum code lying around that hasn’t seen production. Code that isn’t running daily is likely to rot.

In trying to make mistakes cost less, _prevention is better than cure_. There are some mistakes which are rampant but easily avoidable through automation and infrastructure design. We prevented those mistakes.

Our stage nodes can’t talk to our production nodes. We use separate [AWS VPCs](https://aws.amazon.com/vpc/). Even if a configuration were pushed that pointed to db hosts in a different stack, the system would error out. Fail fast rather than corrupt data.

Reducing the cost for bugs mean reducing the time it takes for bug fixes to go live. From the moment of discovery (or introduction), the bug is costing you. The cost may be monetary, or psychological. Users who encounter these bugs may be perplexed, they may be giving up on your services, they may start blaming you, or worse, themselves. The only way to reduce this cost is to promptly take action. To address this, we have built delivery pipelines that deploy to stage as soon as new code enters our repositories and has been unit-tested. The binary that was delivered on stage can directly be used to deploy to production. We have environment agnostic builds. We do this by separating configuration from code. The code that runs on production is the exact same code that runs on stage but with a different set of configuration values.

As of this writing, all our components take at-most 3 minutes from code-push to stage deploy. Deploying to production, I suspect will add another minute, because building and packaging are already taken care of.

***

We want to reclaim simplicity in our software development. We are doing away with steps or processes that aren’t as simple as they can be. If you find this intriguing and you are interested in building things that help expand human knowledge by providing researchers an alternative, beautiful, collaborative experience, get in touch with us at ‘careers’ at `typeset.io’.

This has been part II of ‘Building a fear-free software engineering team’. You may enjoy [part I](fear-free-software-engineering) as well.