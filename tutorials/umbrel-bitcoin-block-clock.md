---
title: DIY Bitcoin Block Clock with Umbrel and Lightning Shell
layout: default
---

1. Get the current block height using `bitcoin-cli`

   `bitcoin-cli getblockcount`

1. Render the current block height by piping the above into `figlet`

   `bitcoin-cli getblockcount | figlet`

1. Execute the above every 10 seconds using `watch`

   `watch -n10 "bitcoin-cli getblockcount | figlet"`
