---
layout: default
---

# Lightning Shell

**Lightning Shell** is a web shell for Bitcoin nodes / personal servers.

It is currently used on [Umbrel](https://getumbrel.com/) and [Citadel](https://runcitadel.space/).

Technically it's a Docker container with [ttyd](https://tsl0922.github.io/ttyd/) and some additional utilities.

## Why?

The web-based tools that come with these personal servers are amazing, but there will always be some case where you want to access the terminal, whether to investigate system performance using standard Linux tools or to run some of the many amazing command-line utilities useful for managing your Lightning Network node.

### Why not just SSH?

SSH works very well indeed for many people.

On one hand, Lightning Shell wants to be an [on-ramp to tinkering](https://ibz.me/posts/tinkerer-friendly-platforms/) for those that are yet to discover the Linux Shell.

On the other hand, Lightning Shell makes it so you don't need to worry about the compilation, packaging and configuration of the various utilities included. When you type `lntop` it just works.

## Installing

The easiest way to install **Lightning Shell** is **from your node's *app store***.

At the opposite end of the spectrum you could simply copy-paste parts of the Dockerfile to build only the tools you want without actually installing Lightning Shell.

There are countless other ways to make use of it in between the two extremes because after all you can fork the repo, customize the Dockerfile, build it and run it yourself.

## Included utilities

- `lncli` (of course)
- [`bos`](https://github.com/alexbosworth/balanceofsatoshis)
- [`charge-lnd`](https://github.com/accumulator/charge-lnd)
- [`igniter`](https://github.com/RooSoft/igniter)
- [`lntop`](https://github.com/edouardparis/lntop)
- [`rebalance-lnd`](https://github.com/C-Otto/rebalance-lnd)
- [`suez`](https://github.com/prusnak/suez)

## Configuration

Running any of the above-mentioned utilities will just work without you having to tell them how to connect to LND.

### How does this work?

Your personal server OS passes the `LND_IP` environment variable and mounts the `lnd` directory under `/lnd` when it launches the **Lightning Shell** Docker container.

There are some additional scripts in `~/.local/bin` named the same as the included utilities, which take care of passing the necessary arguments to the respective utilities.
