---
date: 2023-04-12
title: "Modelix Artifact Re-Grouping and Re-naming "
---

In the last week we re-grouped and re-named several artifacts of modelix platform to more clearly convey their functionality.
For example, the `metamodel-generator` is now named `model-api-gen` illustrating the fact that it generates a model API.
Additionally, we also added correct [Gradle plugin markers](https://docs.gradle.org/current/userguide/plugins.html#sec:plugin_markers) to ease the usage of Gradle plugins in your build scripts.
We also bumped the major version of all modelix core components to indicate the breaking nature this group and name change.

The following table lists all current artifacts, highlighting the changes we made in bold text.

| Old Artifact Group     | Old Artifact Name        | New Artifact Group  | New Artifact Name |
| ---------------------- | ------------------------ | --------------------| ----------------- |
| `org.modelix`          | `model-api`              | `org.modelix`       |`model-api` |
|||||
|` org.modelix`          | `metamodel-export-mps`   | `org.modelix `      | **`metamodel-export`**                        |
|` org.modelix`          | `metamodel-generator`    | `org.modelix `      | **`model-api-gen`**                           |
|` org.modelix`          | `metamodel-runtime`      | `org.modelix `      | **`model-api-gen-runtime`**                   |
|` org.modelix`          | `metamodel-gradle`       | `org.modelix `      | **`model-api-gen-gradle`**                    |
| ---                    | ---                      |    ---              | **`org.modelix.model-api-gen.gradle.plugin`** <br />(new Gradle plugin marker) |
|||||
|` org.modelix`          | `incremental`            | `org.modelix `      | `incremental`                                 |
|` org.modelix`          | `light-model-server`     | `org.modelix `      | **`model-server-lib`**                        |
|` org.modelix`          | `model-server-api`       | `org.modelix `      | `model-server-api`                            |
|` org.modelix`          | `model-server`           | `org.modelix `      | `model-server`                                |
|` org.modelix`          | `model-server-fatjar`    | `org.modelix `      | **`model-server-with-dependencies`**          |
|||||
| `org.modelix`          | `model-client`           | `org.modelix`       | `model-client`                                |
| `org.modelix`          | `light-model-client`     | `org.modelix`       | **`light-model-client`** <br/>(will soon be merged with above) |
|||||
| `org.modelix`          | `gradle-plugin`          | `org.modelix`       | **`model-download-gradle`**                   |
| ---                  | ---                    | ---               | **`org.modelix.mps.model-download`** <br />(new Gradle plugin marker) |
| `org.modelix`          | `mps-model-plugin`       | **`org.modelix.mps`** | **`model-server-sync-plugin`**              |
|||||
| `org.modelix.mpsbuild` | `build-tools`            | **`org.modelix.mps`** | **`build-tools-lib`**                       |
| `org.modelix.mpsbuild` | `gradle-mpsbuild-plugin` | **`org.modelix.mps`** | **`build-tools-gradle`**                    |
| ---                  | `org.modelix.mpsbuild.gradle.plugin`       | ---  | **`org.modelix.mps.build-tools`** <br />(new Gradle plugin marker) |
|||||
| `org.modelix`          | `build-scripts`          | **`org.modelix.mps`**   | **`build-solution`**                         |
|||||
| `org.modelix`          | `headless-mps`           | **`org.modelix.mps`**   | **`headless-runner`**                        |
| `org.modelix`          | `authorization`          | `org.modelix`           | `authorization`                              |
| `org.modelix`          | `web-editors`            | **`org.modelix.mps`**   | **`web-editors-plugin`**                     |
|                        | `ts-model-api`           |                         | `ts-model-api`                               |


In case you are not on the latest modelix version, we encourage you to wait just a little bit longer - we are in the process to transition to a bi-yearly release cycle.
The first release `2023.1` is planned to be launched with the upcoming [MPS Meetup 20203](https://www.eventbrite.co.uk/e/jetbrains-mps-community-meetup-2023-tickets-516733442637).
As a part of this we also plan to provide further documentation on the most important modelix platform components.
Stay tuned!


If you have any questions feel free to reach out via the [#modelix](https://jetbrains-mps.slack.com/archives/C01ADCD6VSM) channel in the MPS Slack or via [mail](mailto:modelix@itemis.com).
