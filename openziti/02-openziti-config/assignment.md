---
slug: openziti-config
id: hb6fft1qt3xl
type: challenge
title: Edit the Configuration
teaser: Change the OpenZiti Controller's configuration.
notes:
- type: text
  contents: Let's change the OpenZiti Controller's configuration and restart the server.
tabs:
- title: Editor
  type: code
  hostname: sandbox
  path: /root/ziti/quickstart/docker/minimal/persistent/
- title: Terminal
  type: terminal
  hostname: sandbox
difficulty: ""
---

## Edit the Configuration

Edit the OpenZiti Controller's configuration file `ctrl.yaml` in the Editor tab to have this new web binding. The `zac` binding makes the Ziti Admin Console available on the specified web listener.

```yaml
      - binding: zac
        options:
          location: /tmp/zac
```

## Build Ziti

Output the built executable to the "build" directory at the top level of the project so it can be copied by this Docker project.

```bash
go build -o ~/ziti/build ~/ziti/...
```

## Build and Run Docker Image

This will copy the built executable from the "build" directory into the container image and run the project.

```bash
docker compose up --build --force-recreate
```
