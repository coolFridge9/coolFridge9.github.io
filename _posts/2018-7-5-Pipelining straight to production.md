---
layout: post
title: Pipelining to Production
---
## Iteration 1: Using Buildkite for Automated Deployment

### overview

![_config.yml]({{ site.baseurl }}/images/Untitled Diagram.jpg)

#### Pipeline step 1:
Code is committed to github.  We had a webhook watching for changes in out github repository on the master branch.
The code is uploaded to the BuildKite API to a BuildKite agent.

![_config.yml]({{ site.baseurl }}/images/webhookGIT.png)
