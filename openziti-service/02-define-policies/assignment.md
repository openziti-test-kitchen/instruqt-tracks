---
slug: define-policies
id: xvudajoxk06e
type: challenge
title: Define Policies
teaser: Create router and service policies.
notes:
- type: text
  contents: Nice! You created an OpenZiti Service with tunneling configs. Now let's
    authorize separate groups of Identities to dial and bind the Service by defining
    policies.
tabs:
- title: Shell
  type: terminal
  hostname: sandbox
difficulty: basic
timelimit: 600
---

## Create Router Policies

Router Policies make it possible to optimize data paths across the OpenZiti network by limiting the Routers that are available to certain Identities and Services.

Authorize all Identities and Services to use all Routers.

```bash
ziti edge create edge-router-policy "default" \
  --edge-router-roles '#all' \
  --identity-roles '#all'

ziti edge create service-edge-router-policy "default" \
  --edge-router-roles '#all' \
  --service-roles '#all'
```

## Show Router Policies

```bash
ziti edge list edge-router-policies
ziti edge list service-edge-router-policies
```

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
