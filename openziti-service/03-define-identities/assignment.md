---
slug: define-identities
id: kju28srmevfk
type: challenge
title: Define Identities
teaser: Define the OpenZiti Identities that will use the Service.
notes:
- type: text
  contents: Great! You've defined policies allowing role 'greeters' to provide the
    hello Service, and role 'members' to consume it. Now let's assign those roles
    to two new Identities.
tabs:
- title: Shell
  type: terminal
  hostname: sandbox
difficulty: basic
timelimit: 600
---

## Create an Identity to Provide the Service

Identities with role `#greeters` are allowed by the Bind Service Policy to host the Service. This means that a tunneler with this role will act as a reverse proxy for the origin specified in the `host.v1` config (`http://hello:8000`).

```bash
ziti edge create identity "Alice" \
  --jwt-output-file /tmp/alice.jwt \
  --role-attributes greeters
```

## Create an Identity to Access the Service

Identities with role `#members` are allowed by Dial Service Policy to connect to the Service with the address specified in the `intercept.v1` config (`http://hello.private`).

```bash
ziti edge create identity "Bob" \
  --jwt-output-file /tmp/bob.jwt \
  --role-attributes members
```
