---
slug: define-service-configuration
id: jacnp1s2n0rp
type: challenge
title: Define Service
teaser: Configure a Service's dial and bind parameters.
notes:
- type: text
  contents: |
    As one of the unofficial greeters, Alice has a "hello" web server to share with new members. Let's create tunneling configs and use them to define an OpenZiti Service for the "hello" server.
tabs:
- title: Alice
  type: terminal
  hostname: alice
difficulty: basic
timelimit: 600
---

Create an OpenZiti Service configured with tunneling parameters for sharing the hello demo web server.

## Check the Hello Server Origin

This is the web server origin that will be shared via the OpenZiti Service that you configure in this challenge.

```bash
curl -s http://hello:8000
```

## Log in

```bash
ziti edge login quickstart:1280 -u admin -p admin -y
```

## Create the Dial Config

Config type `intercept.v1` stores the tunneling parameters for Identities with dial permission on a Service.

```bash
ziti edge create config "hello-intercept" intercept.v1 \
  '{"protocols":["tcp"],"addresses":["hello.private"], "portRanges":[{"low":80, "high":80}]}'
```

## Show the Dial Config

```bash
ziti edge show config "hello-intercept"
```

## Create the Bind Config

Config type `host.v1` stores the tunneling parameters for the Identities with bind permission on a Service.

```bash
ziti edge create config "hello-host" host.v1 \
  '{"protocol":"tcp", "address":"hello","port":8000}'
```

## Show the Bind Config

```bash
ziti edge show config "hello-host"
```

## Create the Service

```bash
ziti edge create service "hello-service" \
  --configs hello-intercept,hello-host \
  --role-attributes greeting-services
```

## Show the Service

```bash
ziti edge list services 'name="hello-service"'
```
