---
date: 2023-11-02
title: "Modelix Platform Release 23.2"
---

We are happy to announce the autumn release of the modelix platform: **`23.2`**

The versions bundled in this release are:

```
modelixCoreVersion = 3.12.1
incrementalVersion = 0.2.0
buildToolsVersion = 1.1.0
modelixMPSPatchVersion = 157
```

If you want to know how to use this platform in your Gradle build, check out the corresponding [documentation](https://docs.modelix.org/modelix/23.2/platform/howto/usage-platform.html).

- [Feature Highlights](#feature-highlights)
  - [ModelQL](#modelql)
  - [Model Client as NPM Package (experimental)](#model-client-as-npm-package-experimental)
  - [Vue.js Bindings (experimental)](#vuejs-bindings-experimental)
  - [MPS Model Adapters](#mps-model-adapters)
  - [Bulk Model Synchronization Plugin (experimental)](#bulk-model-synchronization-plugin-experimental)
- [Development Insights](#development-insights)
  - [New Approach to MPS-Related Components](#new-approach-to-mps-related-components)
  - [Contribution Guide](#contribution-guide)
  - [Marking Experimental Features](#marking-experimental-features)
  - [Extending Automation](#extending-automation)
- [What's To Come](#whats-to-come)

# Feature Highlights

## ModelQL

The [ModelQL query language](https://docs.modelix.org/modelix/23.2/core/explanation/modelql.html) provides a dynamic way of loading parts of the model on demand while reducing the number of requests to a minimum.

## Model Client as NPM Package (experimental)

The previously existing [model client](https://github.com/modelix/modelix.core/tree/modelix-23.2/model-client) is now also published as [`@modelix/model-client` NPM package](https://artifacts.itemis.cloud/service/rest/repository/browse/npm-open/%40modelix/model-client/).

The exposed API is minimal and experimental. 
In the future, we want to make more features from the Kotlin model client directly accessible from the exposed API in the NPM package.

## Vue.js Bindings (experimental)

Built upon [`@modelix/model-client`](https://artifacts.itemis.cloud/service/rest/repository/browse/npm-open/%40modelix/model-client/) we created a library to interact with models through [Vue.js](https://vuejs.org/).

With [`@modelix/vue-model-api`](https://docs.modelix.org/modelix/23.2/core/reference/component-vue-model-api.html) we are currently building sample projects with Vue.js.
After that, we want to stabilize the API and show you how you can use it for your projects.

## MPS Model Adapters

We created [adapters](https://github.com/modelix/modelix.core/tree/modelix-23.2/mps-model-adapters) between MPS and modelix.
They forward changes made to a model through the [model-api of modelix](https://docs.modelix.org/modelix/23.2/core/reference/component-model-api.html) to the [Open API of MPS](https://www.jetbrains.com/help/mps/open-api-accessing-models-from-code.html).
They are compatible with all MPS versions that modelix currently supports.

With their help, it is possible to implement access and synchronization from modelix components to MPS.
The [bulk-model-sync Gradle Plugin](#bulk-model-synchronization-plugin-experimental) is an example component that uses them.

## Bulk Model Synchronization Plugin (experimental)

The [bulk-model-sync Gradle Plugin](https://docs.modelix.org/modelix/23.2/core/reference/component-bulk-model-sync-gradle.html) allows bulk synchronization of models between MPS and a [model-server](https://docs.modelix.org/modelix/23.2/core/reference/component-model-server.html).
The plugin applies changes incrementally, and can be run in existing CI systems to schedule and run the synchronization in both directions.
This way you can implement a custom Git Integration tailored to your needs.

The plugin is considered unstable, but will be stabilized soon.

# Development Insights

## New Approach to MPS-Related Components


Up until now, we built and released MPS-specific components for each MPS version individually.
Going forward, we want to release single components, which are compatible with all MPS versions that are currently supported by modelix.
The first component to follow this new approach is [mps-model-adapters](#mps-model-adapters)

To achieve that, we separate code in MPS solutions from support library code wherever possible.
Also, we are developing upcoming MPS plugins as IntelliJ plugins instead of MPS plugins.
This reduces the overhead required for updating and maintenance.

## Contribution Guide

We created a [contribution guide](https://docs.modelix.org/modelix/main/main/contribute.html) to help new contributors.

## Marking Experimental Features

From now on, we mark experimental features clearly.
You can read about it in more detail in our [documentation](https://docs.modelix.org/modelix/main/main/development.html#experimental_features)

## Extending Automation

In our automation, we introduced static code analysis, dependency updating and security checking.
This aims to increase developer velocity, reduce bugs and provide more security for our users. 

# What's To Come

We are in the process of planning our [roadmap](https://docs.modelix.org/modelix/main/main/roadmap.html) and are aiming to update it this year.