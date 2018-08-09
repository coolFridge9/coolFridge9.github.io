---
layout: post
title: Making an Express App
---

The basic structure is that the user connects to the main app and the main app has subapps which distinuish the urls.

![_config.yml]({{ site.baseurl }}/images/expressImage.png)

Basically, an external party, such as, a user or a regular health checker (datadog) will hit the main app through the load balancer. The app will use the url to determine which subapp to call which uses controllers to determine the functionality.  

The load balancer will only connect to instances which are healthy.  An external tool called datadog will run a system health check frequently. A system health check checks that the whole system works, such as, the dependencies are up and running.
