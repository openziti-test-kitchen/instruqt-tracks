---
slug: connect-with-a-tunneler
id: nkixhn46p4nn
type: challenge
title: Connect with a Tunneler
teaser: Everything is ready. Now lets go to a new computer and connect to the Hello
  Service.
notes:
- type: text
  contents: Give Bob his enrollment token so he can connect to the hello Service.
tabs:
- title: Bob
  type: terminal
  hostname: bob
- title: Alice
  type: terminal
  hostname: alice
difficulty: basic
timelimit: 600
---

The OpenZiti Tunneler (`ziti-edge-tunnel`) has been pre-installed. When an Identity is added, it will configure Bob's computer to access any allowed Services by adding their addresses to Ziti DNS.

## Too Soon

Note that the hello Service is not yet available.

```bash
curl -m1 http://hello.private
```

## Add Bob's Identity

```bash
ziti-edge-tunnel add --identity Bob --jwt "[[ Instruqt-Var key="BOB_JWT" hostname="alice" ]]"
```

## Welcome, Bob

```bash
curl http://hello.private
```
