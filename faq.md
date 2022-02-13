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

Lightning Shell doesn't support `cron`, but Umbrel does. You can edit the crontab using `crontab -e` (after you have SSHed into your Umbrel).

The only tricky part is executing Lightning Shell commands from Umbrel. You need to get the ID of the Docker container, then execute the command using `docker exec`.
