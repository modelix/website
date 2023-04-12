---
title: About Modelix
linkTitle: About
menu:
  main:
    weight: 10
layout: docs
---


{{% blocks/cover title="About Modelix" height="auto" %}}

The modelix project develops a next generation language workbench that is native to the web and the cloud, inspired by [this document](http://voelter.de/data/pub/APlatformForSystemsAndBusinessModeling.pdf). On the path to this final vision, the short-term goal is to use MPS as the backend. To this end, we currently develop two components:

* Database/Cloud storage for MPS models with realtime collaboration
* Server-based execution of MPS and browser-based editors

Read on to find out more, or visit our [documentation](https://docs.modelix.org/) to get started!
{{% /blocks/cover %}}

{{% blocks/section type="section" color="primary" %}}
As a cornerstone modelix relies on running a set of MPS instances on the server. These provide the language services available in MPS, including scoping and code completion, type checking or code generation.

Because we rely on MPS, language development can continue in MPS and existing MPS languages can be used immediately in modelix. To support web-based editing, modelix “forwards” the MPS editors to the browser; again, any notation that works in MPS will also work in modelix. To support scaling of server-side resources and to allow for failover if an MPS instance crashes, the models are stored in a shared database. This shared database is also the key for collaborative real-time editing.

As a side effect of this architecture, a user of a regular client-side MPS can connect to that database as well, getting the benefits of real-time collaboration even without the web-based interface.

Modelix can either be run locally via Docker, or in the cloud via Kubernetes.

On a parallel track, the development of an API for accessing the models in the shared database has started. This will be the basis for developing services which analyse, execute or otherwise modify models without going through MPS. In addition, this will be the basis for the REST-based bulk model APIs mentioned above.

{{% /blocks/section %}}

{{% blocks/section type="section" color="white" %}}

# A vision for the future

A while ago we wrote a [vision whitepaper](https://voelter.de/data/pub/APlatformForSystemsAndBusinessModeling.pdf) that outlines where we think a language workbench of the future should go. I’ll summarize it here briefly, and then discuss our concrete steps towards this vision in the next section.

## Tool Architecture

At the core of the kind of industrial-scale modeling tools the vision paper describes is a distributed database that stores graphs. These graphs represent both the front-end models edited by users, as well as intermediate models or results of analyses that are computed by the tool itself.

For every edit operation the user performs via the browser on whatever model she edits, the editor sends a change event to the repository that updates the master model. Transformation services, directly connected to the repository, listen to particular kinds of change events, and when they see one, they incrementally update the result models they are responsible for. This update might involve the execution of a test case (updating the result data), rerunning of a quick performance analysis or something as mundane as the type checks for the user-facing model. The updates to the result models are then transferred back to the client side editor, if the client has subscribed to the particular model.

Services might also execute longer-running analyses, such as model checking a complex state machine or generating a whole bunch of Java. At the core, however, the platform is designed to support this incremental, real-time update of computed data to enable liveness.

Those deltas are also the basis for deconflicing concurrent edits to the same nodes, which in turn is the basis for Google Doc-style real-time collaboration.

## A set of Editors

Of course not all editors will be delta-oriented, and there will also be other clients that just want to work with snapshots of models – user-created or computed. For this purpose, the tool will provide REST APIs for reading and writing complete models via JSON-based bulk data. A particularly important example of such a client is a CI server that grabs models and then runs maybe a code generator and a subsequent compiler to create the artifacts ultimately required by the users.

Usable and powerful editors are certainly crucial for this vision, not least because they are the primary user-facing components of the system. However, for this same reason, editors will exhibit the largest variety: for simple languages, we want simple editors with very little if any chrome; more sophisticated systems perhaps need more powerful editors with quick fixes, refactorings and a whole array of buttons and menus around it. While out-of-the-box default editors are needed, we expect an ecosystem of different styles of editors to be developed over time.

The system should also support some of the standard functionalities of enterprise systems, such as permission checking, auditing and payment.

## Language Development

The meta level, where language engineers develop the languages, would be nice to also have available in the web. However, for the time being, it is acceptable to continue this work in a “fat” IDE: there are comparatively few people who do this work, and they are developers. From the perspective of language engineering – the overall set of language features, the range of notations as well as the support for language modularity should be similar to (or potentially better than) MPS.

{{% /blocks/section %}}

{{% blocks/section type="section" color="primary" %}}

# Where are we

Modelix is currently a prototype that demonstrates the feasibility of the idea: it wasn’t obvious that running MPS in the cloud, managed by Kubernetes, and forwarding the MPS-rendered editor into the browser would be feasible. Turns out it is, at least as a pragmatic first step.

We are currently in the process of setting up a modelix instance in the cloud, so if you want to play with it, you can get in touch and we’ll give you access.

{{% /blocks/section %}}
