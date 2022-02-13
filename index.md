---
layout: default
---

# Lightning Shell

**Lightning Shell** is a shell for Bitcoin nodes / personal servers.

It is currently used on [Umbrel](https://getumbrel.com/) and [Citadel](https://runcitadel.space/).

Technically it's a Docker container with [ttyd](https://tsl0922.github.io/ttyd/) and additional utilities.

## Included utilities

### General Lightning node management
- `lncli` & [`bos`](https://github.com/alexbosworth/balanceofsatoshis) - The classics
- [`lntop`](https://github.com/edouardparis/lntop) - LN terminal dashboard

### Fee management
- [`charge-lnd`](https://github.com/accumulator/charge-lnd) - Simple policy based fee manager
- [`suez`](https://github.com/prusnak/suez) - Tool for pretty printing and optimizing channels

### Rebalancing tools
- [`rebalance-lnd`](https://github.com/C-Otto/rebalance-lnd)
- [`igniter`](https://github.com/RooSoft/igniter) - Circular rebalancing by sending a payment back to yourself using a specific route
- [`perfectly-balanced`](https://github.com/cuaritas/perfectly-balanced) - Script to make your LND node perfectly balanced

### Bitcoin tools
- [`btc2fiat`](https://github.com/ibz/btc2fiat) - Bitcoin price expressed in fiat currency. As simple as that.

### Data tools
- `bc` - An arbitrary precision calculator language
- [`csview`](https://github.com/wfxr/csview) - A high performance CSV viewer
- [`jq`](https://stedolan.github.io/jq/) - JSON processor
- [`sc-im`](https://github.com/andmarti1424/sc-im) - Spreadsheet program for your terminal

### Networking
- [`dog`](https://github.com/ogham/dog) - A command-line DNS client
- [`gping`](https://github.com/orf/gping) - Ping, but with a graph
- [`links`](http://links.twibright.com/) - Web browser
- [`oha`](https://github.com/hatoo/oha) - HTTP load generator with TUI animation

## Installation

The easiest way to install **Lightning Shell** is **from your node's *app store***.

At the opposite end of the spectrum you could simply copy-paste parts of the Dockerfile to build only the tools you want without actually installing Lightning Shell.

There are countless other ways to make use of it in between the two extremes because after all you can fork the repo, customize the Dockerfile, build it and run it yourself.

## Configuration

Running any of the included utilities will just work without you having to tell them how to connect to LND.

### How does this work?

Your personal server OS passes the `LND_IP` environment variable and mounts the `lnd` directory under `/lnd` when it launches the **Lightning Shell** Docker container.

There are some additional scripts in `~/.local/bin` named the same as the included utilities, which take care of passing the necessary arguments to the respective utilities.
