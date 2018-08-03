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

#### Pipeline step 2:
An image is created (An empty container).  I founds out later that this isn't a good idea.  I should have a pre-baked container uploaded so less things can go wrong. (such as dotnet updating with a bug or aws)

![_config.yml]({{ site.baseurl }}/images/DOcker2.png)

#### Pipeline step 3: Run the dockerfile and run the tests
Runing the dockerfile installs the dependancies for the application to run in the docker.  In this step we ran the tests written (we only did unit tests but integration tests are important too) If the tests passed, the deployment continued.

#### Pipeline step 4: Build and publish the app
Publish the final app into an s3 bucket.  
![_config.yml]({{ site.baseurl }}/images/Screen Shot 2018-08-03 at 1.37.20 PM.png)

#### Running the published app
Add some scripts to the autoscalling group which pull the app from the bucket on the ec2 start up and runs the app.

![_config.yml]({{ site.baseurl }}/images/Autoscalling G.png)

