---
title: FAQ
layout: default
---

<h2 id="on_start">How can I run a script when the container is started?</h2>

NB: This feature was added in [v0.1.7](/history#v0.1.7).

1. Create a file called `on_start.sh` under `/data` and make it executable. Make sure it has the correct [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix))!

   `echo '#!/bin/sh' > /data/on_start.sh && chmod +x /data/on_start.sh`

1. Now go ahead and edit this file, adding your custom commands.
