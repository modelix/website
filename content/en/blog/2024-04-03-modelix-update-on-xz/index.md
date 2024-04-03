---
date: 2024-04-03
title: "Modelix Update on XZ Utils Backdoor"
---

Modelix images are not affected by the [XZ Utils backdoor](https://en.wikipedia.org/wiki/XZ_Utils_backdoor) (CVE-2021-44228).

Our images have versions of `liblzma` ranging from `5.2.2` to `5.4.1`.
So no image has the vulnerable version `5.6.0` or `5.6.1`.
Also, no image has an SSH server installed.

If you have any questions, feel free to reach out via the [#modelix](https://jetbrains-mps.slack.com/archives/C01ADCD6VSM) channel in the MPS Slack.