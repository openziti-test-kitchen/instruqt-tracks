---
slug: openziti-run
id: xxih2zdsuxug
type: challenge
title: Run OpenZiti
teaser: Run a Minimal OpenZiti Network
notes:
- type: text
  contents: |+
    # Run the OpenZiti Edge Quickstart Command

    The quickstart command runs a minimal OpenZiti network as a single process. This presents two TLS server ports: one each for the OpenZiti Controller (1280/tcp) and Router (3022/tcp).

tabs:
- title: Terminal
  type: terminal
  hostname: sandbox
difficulty: ""
timelimit: 600
---

## 🧪 Run the `ziti edge quickstart` command with Docker

Let's run the quickstart as a Docker project.

```bash
docker compose up --detach
```

## 💡Check the Log

After a few seconds, the log will show that the router is online with a message like this.

> INFO ziti/router/handler_edge_ctrl.(*apiSessionAddedHandler).applySync: finished sychronizing api sessions

```bash
docker compose logs --follow
```

Press Ctrl-C to stop following the logs.

## 💡Log in with ziti CLI

OpenZiti is running in the background. Let's log in.

```bash
ziti edge login 127.0.0.1:1280 -u admin -p admin -y
```

## 💡 List Edge Routers

Once authenticated, let's see if our router is online.

```bash
ziti edge list edge-routers
```

You should see output similar to this:

```text
╭────────────┬───────────────────┬────────┬───────────────┬──────┬────────────╮
│ ID         │ NAME              │ ONLINE │ ALLOW TRANSIT │ COST │ ATTRIBUTES │
├────────────┼───────────────────┼────────┼───────────────┼──────┼────────────┤
│ pv.u-vlmYU │ quickstart-router │ true   │ true          │    0 │ public     │
╰────────────┴───────────────────┴────────┴───────────────┴──────┴────────────╯
results: 1-1 of 1
```

## 💡List Identities

```bash
ziti edge list identities
```

You should see output similar to this:

```text
╭────────────┬───────────────────┬─────────┬────────────┬─────────────╮
│ ID         │ NAME              │ TYPE    │ ATTRIBUTES │ AUTH-POLICY │
├────────────┼───────────────────┼─────────┼────────────┼─────────────┤
│ ZGyh-3lNY  │ Default Admin     │ Default │            │ Default     │
│ pv.u-vlmYU │ quickstart-router │ Router  │            │ Default     │
╰────────────┴───────────────────┴─────────┴────────────┴─────────────╯
results: 1-2 of 2
```


## 🏁 Finish

To complete the
challenge, press **Check**."
