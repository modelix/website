---
date: 2022-09-26
title: "Modelix Update on JetBrain's Projector"
---

On March 11 2021 JetBrains [announced the initial release of Projector](https://blog.jetbrains.com/blog/2021/03/11/projector-is-out/). It can be used to run JetBrains IDEs and Swing apps remotely over the network.
Just recently JetBrains **[announced the suspension of Projector as its own standalone product](https://lp.jetbrains.com/projector/)**. There are components in modelix which make use of Projector so consequently the question arises how this change affects the support in contexts such as Modelix?

This announcement by JetBrains might seem rather sudden. In fact, two client implementations for Projector exist, a browser based one (the now discontinued Projector) and a dedicated one called *[Gateway](https://www.jetbrains.com/remote-development/gateway/)*. The browser based one has some limitations and Gateway provides the better experience (for our use cases the browser limitations are not relevant, because we do not want the full IDE experience anyways). That's the reason why JetBrains decided to discontinue developing the browser based one.

From the perspective of modelix this announcement does not pose any problems. At the moment we simply use projector for embedding MPS editors into the browser and it is not our long term goal to keep it this way. We will be replacing these embedded editors by editor implementations that use HTML/JS and provides a better integration with other web frameworks.

However, connecting to a remote MPS instance via managed by the server might still provide some benefits for language developers, but then the solution for this use case is to have a provider plugin for Gateway instead of using the browser based Projector. For now, Projector still works and is still better than our own attempts at providing a similar feature. If needed we can even maintain [a fork](https://github.com/modelix?q=projector) for the transitional period.

If you have any questions feel free to reach out via the [#modelix](https://jetbrains-mps.slack.com/archives/C01ADCD6VSM) channel in the MPS Slack.
