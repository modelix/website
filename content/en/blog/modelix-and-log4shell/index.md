---
date: 2021-12-14
title: "Modelix Update on Log4Shell"
---

A short update on the vulnerability called "[Log4Shell](https://en.wikipedia.org/wiki/Log4Shell)" (CVE-2021-44228) from the modelix team:

As you most likely have heard already there is a vulnerability in the popular logging framework log4j affecting many projects, especially services logging HTTP requests. For more details on the vulnerability see the log4J [announcement](https://logging.apache.org/log4j/2.x/security.html).

Since modelix services can face the public internet you might ask yourself if you are affected when running modelix. The good news is **you are not affected** by Log4Shell when you are using modelix. Modelix doesn't use the particular versions on log4J that are vulnerable. 

As part of a review of our dependencies we discovered that we are in fact using log4J 1.2.17 which isn't affected. But log4j 1.x is end of life since 2015 and doesn't receive further updates. We mitigated this by [replacing log4j with logback](https://github.com/modelix/modelix/pull/141) in the places where we used it. [Logback](https://logback.qos.ch) is a well maintained log4j API 1.x compatible open source project. As of now we do not think any version of modelix in its default configuration is vulnerable to the known issues of log4j 1.x. The issues are affecting the SocketServer and could result in remote code execution. The modelix default configuration does not load these classes. 
    
### A Note on MPS 

Modelix depends on MPS for the browser based MPS editor and via projector. MPS and other IntelliJ based products from JetBrains aren't [affected by Log4Shell](https://blog.jetbrains.com/blog/2021/12/13/log4j-vulnerability-and-jetbrains-products-and-services/). MPS and the IntelliJ Platform are using log4j 1.2.17 at the moment. Similar to modelix their default configuration does not expose the vulnerable parts of log4j. 

JetBrains is [actively working](https://youtrack.jetbrains.com/issue/IDEA-265069) on replacing log4j 1.x. 

If you have any questions feels free to reach out via the [#modelix](https://jetbrains-mps.slack.com/archives/C01ADCD6VSM) channel in the MPS Slack.
