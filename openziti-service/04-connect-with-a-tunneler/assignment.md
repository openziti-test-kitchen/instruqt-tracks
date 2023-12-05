---
slug: connect-with-a-tunneler
id: nkixhn46p4nn
type: challenge
title: Connect with a Tunneler
teaser: Everything is ready. Now lets go to a new computer and connect to the Hello
  Service.
notes:
- type: text
  contents: Connect to the Hello Service with an OpenZiti tunneler running on a different
    machine.
tabs:
- title: Shell
  type: terminal
  hostname: bob
difficulty: basic
timelimit: 600
---

The OpenZiti Tunneler (`ziti-edge-tunnel`) has been pre-installed on this host as a system service. When an Identity is added, it will this host to access any allowed Services by adding their addresses to Ziti DNS.

## Add Bob's Identity to the Running Tunneler

```bash
ziti-edge-tunnel add --jwt "$(< /tmp/bob.jwt)" --identity Bob
```

The JWT enrollment token looks like this:
> [[ Instruqt-Var key="BOB_JWT" hostname="sandbox" ]]

## Connect

```bash
curl -s http://hello.private
```
