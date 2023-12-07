---
slug: define-identities
id: kju28srmevfk
type: challenge
title: Define Identities
teaser: Define the OpenZiti Identities that will use the Service.
notes:
- type: text
  contents: |
    You've defined policies allowing role 'greeters' to host the hello Service, and role 'members' to consume it. Now let's assign those roles to the appropriate Identities. Alice will delegate hosting the Service to the router that is already running in the environment by assigning role "greeters." Bob is a new member that will consume the Service.
tabs:
- title: Alice
  type: terminal
  hostname: alice
difficulty: basic
timelimit: 600
---

## Grant the `greeters` role to the Router's Identity

The demo network comes with a Router. Let's give it Bind permission for Service `hello-service` by granting the `#greeters` role. This causes the assigned Identity to provide a TCP reverse proxy for the origin specified in the `host.v1` config (`hello:8000`).

```bash
ziti edge update identity "quickstart-router" \
  --role-attributes greeters
```

## Create an Identity to Access the Service

Identities with role `#members` are allowed by Dial Service Policy to connect to the Service with the address specified in the `intercept.v1` config (`hello.private:80`).

```bash
ziti edge create identity "Bob" \
  --jwt-output-file /tmp/bob.jwt \
  --role-attributes members
```

No need to save the JWT enrollment token for this exercise. It will be copied to the next challenge for you.
