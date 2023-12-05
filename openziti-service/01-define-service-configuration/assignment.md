---
slug: define-service-configuration
id: jacnp1s2n0rp
type: challenge
title: Define Service Configuration
teaser: Configure a Service's dial and bind parameters.
notes:
- type: text
  contents: |
    Log in and create the two necessary tunneling configs for your OpenZiti Service: intercept.v1 (dial side) and host.v1 (bind side).
tabs:
- title: Shell
  type: terminal
  hostname: sandbox
difficulty: basic
timelimit: 600
---

## Log in

```bash
ziti edge login quickstart:1280 -u admin -p admin -y
```

## Create the Dial Config

Config type `intercept.v1` stores the parameters for Identities with dial permission on a Service.

```bash
ziti edge create config "hello-intercept" intercept.v1 \
    '{"protocols":["tcp"],"addresses":["hello.private"], "portRanges":[{"low":80, "high":80}]}'
```
