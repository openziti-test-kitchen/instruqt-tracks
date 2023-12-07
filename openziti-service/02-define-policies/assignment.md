---
slug: define-policies
id: xvudajoxk06e
type: challenge
title: Define Policies
teaser: Create router and service policies.
notes:
- type: text
  contents: |
    Nice! We created an OpenZiti Service with tunneling configs for clients to dial and hosts to bind. Now let's authorize both by defining policies.
tabs:
- title: Alice
  type: terminal
  hostname: alice
difficulty: basic
timelimit: 600
---

## Create Service Policies

Service Policies authorize Identities to `Bind` or `Dial` Services.

```bash
ziti edge create service-policy "greeting-services-providers" Bind \
  --service-roles '#greeting-services' \
  --identity-roles '#greeters'

ziti edge create service-policy "greeting-services-consumers" Dial \
  --service-roles '#greeting-services' \
  --identity-roles '#members'
```

## Show Service Policies

```bash
ziti edge list service-policies
```
