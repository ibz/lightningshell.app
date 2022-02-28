---
title: FAQ
layout: default
---

<h2 id="data">Where can I store my files?</h2>

The best place to store files you don't want to lose is under `/data`. This directory is mounted from your personal server and the contents is not lost on OS update.

If the files are truly important, you may also want to back them up. You could for example schedule a `rsync` to some other machine.

<h2 id="on_start">How can I run a script when the container is started?</h2>

NB: This feature was added in [v0.1.7](/history#v0.1.7).

1. Create a file called `on_start.sh` under `/data` and make it executable. Make sure it has the correct [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix))!

   `echo '#!/bin/sh' > /data/on_start.sh && chmod +x /data/on_start.sh`

1. Now go ahead and edit this file, adding your custom commands.

<h2 id="cron">How can I schedule a command to be run automatically?</h2>

Lightning Shell doesn't support `cron`, but your host OS such as Umbrel does. You can edit the crontab using `crontab -e` (after you have SSHed into your Umbrel!).

You can then use [`lsh_exec_ni.sh`](/faq#lsh_exec.sh) to execute Lightning Shell commands from Umbrel's `cron`. If you want the data returned by these commands to be available in Lightning Shell, you just have to save it under `/mnt/data/umbrel/app-data/lightning-shell/data/`.

For example, you could do the following:

1. create a file `btc.csv`

   `echo date,price > /data/btc.csv` (in Lightning Shell)

2. periodically save the bitcoin price to `btc.csv` by adding the following to your Umbrel's crontab

   ```
    echo `date +"%Y-%m-%d %H:%M"`","`/mnt/data/umbrel/app-data/lightning-shell/data/lsh_exec.sh btc2fiat` >> /mnt/data/umbrel/app-data/lightning-shell/data/btc.csv
   ```

3. view the file using `csview` in Lightning Shell

   `csview /data/btc.csv`

<h2 id="lsh_exec.sh">What are lsh_exec.sh / lsh_exec_ni.sh?</h2>

NB: `lsh_exec.sh` was added in [v0.1.8](/history#v0.1.8) and `lsh_exec_ni.sh` was added in [v0.1.10](/history#v0.1.10).

These scripts can be used to execute Lightning Shell commands from Umbrel. For example you can run `suez` from Umbrel using the following:

```
/mnt/data/umbrel/app-data/lightning-shell/data/lsh_exec.sh suez
```

The difference between the two is that `lsh_exec.sh` passes `-it` to Docker while `lsh_exec_ni.sh` does not. The latter is to be used from `cron` scripts, for example.
