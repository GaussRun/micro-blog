---
title: "Wait for the shell prompt before typing into a new tmux pane"
tags: [tmux]
---
I created a tmux pane and immediately sent a command with `send-keys`. The terminal echoed it raw, then the shell drew its prompt and showed the command again.

Fix: wait until the pane shows something (up to 1.5 s), then send the keys.
