# Lightning Shell

**Lightning Shell** is a web shell for Bitcoin nodes / personal servers.

Currently, it is used on [Umbrel](https://getumbrel.com/) and [Citadel](https://runcitadel.space/).

Technically it's a Docker container with [ttyd](https://tsl0922.github.io/ttyd/) and some additional utilities.

## Why?

The web-based tools that come with these personal servers are amazing, but there will always be some case where you want to access the terminal, whether to investigate system performance using standard Linux tools or to run some of the many amazing command-line utilities useful for managing your Lightning Network node.

### Why not just SSH?

SSH works very well indeed. The problem is the compilation, packaging and configuration of the various utilities.

Let's say you compile `lntop` and make it work on your node - it's not hard, but it may be a bit of a challenge for a complete beginner. Then you want to update the OS and reflash the SD card - _bang_ you just lost `lntop`. Good luck bringing it back if you didn't write down the exact steps.

And every such utility has its own quirks about how it needs to be installed and configured. You spend time figuring it all out, then you lose it all with a simple reflash.

An alternative is, of course, to keep scripts of the exact steps so you can re-run them when needed. And this is exactly what **Lightning Shell** does: it builds and packages various command line utilities so you don't have to.

## Installing

The easiest way to install **Lightning Shell** is **from your node's *app store***.

At the opposite end of the spectrum, you could simply copy-paste parts of the Dockerfile to build only the tools you want without actually installing Lightning Shell.

There are countless other ways to make use of it in between the two extremes: you could for example run the pre-built Docker image yourself, you could fork the repo and customize the Docker file... It's all up to you.

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

Then, there are some additional scripts in `~/.local/bin` named the same as the included utilities, which take care of passing the necessary arguments to the respective utilities.
