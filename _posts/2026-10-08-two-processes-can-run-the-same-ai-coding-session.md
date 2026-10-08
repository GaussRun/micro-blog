---
title: "Two processes can run the same AI coding session"
tags: [agents]
---
Resume a coding agent session in a second terminal while the first is still running, and you have two processes writing the same transcript.

My session finder kept one process per session id. So it showed one location, and "take over" stopped one process and resumed while the other kept writing.

Now it keeps every process per session, doesn't count zombies as live, and "take over" stops all of them, checks every pid is gone and that nothing else picked the session up, and only then resumes. If one survives, it resumes nothing and names the survivor.
