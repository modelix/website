---
date: 2024-05-16
title: "Modelix Platform Release 24.1"
---

Version **`24.1`** of the modelix platform is out now!
The platform is now independent of the MPS version and works with all supported MPS versions.
Simply use `org.modelix:platform:24.1.0` in your build scripts.

The versions bundled in this release are:

```
modelixCoreVersion = 7.3.0
incrementalVersion = 0.2.0
buildToolsVersion = 1.5.0
mpsPluginsVersion = 0.7.1
```
A more detailed list of the components is available [here](https://github.com/modelix/modelix.platform/blob/docs/release/24.1/gradle/libs.versions.toml).

If you want to know how to use this platform in your Gradle build, check out the [corresponding usage documentation](https://docs.modelix.org/modelix/24.1/platform/howto/usage-platform.html).


- [Feature Highlights](#feature-highlights)
  - [Support for newer MPS Versions](#support-for-newer-mps-versions)
  - [Stabilization of the Bulk Model Synchronization Plugin](#stabilization-of-the-bulk-model-synchronization-plugin)
- [Experimental Features](#experimental-features)
  - [MPS Sync Plugin (experimental)](#mps-sync-plugin-experimental)
  - [New Adapter for the LionWeb Bulk API (experimental)](#new-adapter-for-the-lionweb-bulk-api-experimental)
- [What's next](#whats-next)

# Feature Highlights

## Support for newer MPS Versions

Modelix components are now compatible with MPS 2021.1 - 2023.2.
To reduce the required maintenance effort, we decided to drop support for MPS 2020.3.
While some use cases might still work with 2020.3, we highly recommend using a more recent MPS version.

## Stabilization of the Bulk Model Synchronization Plugin

The [bulk-model-sync Gradle plugin](https://docs.modelix.org/modelix/24.1/core/reference/component-bulk-model-sync-gradle.html) allows the bulk synchronization of models between MPS and a [model-server](https://docs.modelix.org/modelix/24.1/core/reference/component-model-server.html).
The plugin is now stable.
However, we will continue to improve its performance in the future.

# Experimental Features

## MPS Sync Plugin (experimental)

A new Kotlin-based MPS Sync Plugin is in the making, which will allow you to bind local MPS repositories to remote model-server repositories.
You will be able to seamlessly exchange model data between MPS and the model-server in an interactive fashion.
Changes performed on one side will be automatically synchronized to the other side.
For non-interactive workflows like CI tasks use the [bulk-model-sync Gradle plugin](https://docs.modelix.org/modelix/24.1/core/reference/component-bulk-model-sync-gradle.html).

## New Adapter for the LionWeb Bulk API (experimental)

If you are interested in the integration of other modeling technologies than MPS then check out the [LionWeb](https://lionweb.io/) initiative (short for Language Interfaces on the web).
The modelix team co-authored and is involved with LionWeb.

A first version of the [lionweb-modelix-adapter](https://github.com/LionWeb-io/lionweb-modelix-adapter) has been made available on the LionWeb GitHub.
It allows using the model-server with the LionWeb Bulk API, but comes with limitations detailed in the README.
We recommend using the modelix model-api to make use of advanced model-server features such as real-time collaboration.

# What's next

Keep an eye on our new [Modelix LinkedIn Page](https://www.linkedin.com/company/modelixweb/), where we are regularly sharing Modelix-related content including additional development insights.

