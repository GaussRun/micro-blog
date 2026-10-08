---
title: "What I want from a \"find that agent session\" tool"
tags: [agents, search]
---
I run a lot of coding agent sessions across folders, terminals and a few VMs. The question I keep asking: where is the session that worked on X, is it still running, and can I get back into it?

Built in, `claude --continue` reopens the last session in the current folder and `claude --resume` gives you a picker. Fine if you remember the folder.

What already exists beyond that (as of late August 2026):

- [memex](https://github.com/nicosuave/memex): the big one, 168 stars. Rust, searches Claude Code, Codex, Cursor, OpenCode, Copilot CLI and more, resumes sessions, and queries other machines over SSH.
- A handful of small herdr plugins: session-digger, herdr-omnisearch, herdr-convo-index, herdr-plugin-vault, herdr-vaultr, herdr-opencode-sessions.

My requirements, roughly in order:

1. Search by what I typed, across every folder and machine, not just this one.
2. Say whether the session is running right now, and where (pane, terminal, pid). Enter jumps there.
3. If it is closed, resume it. If only the history survived and the transcript is gone, say so instead of failing.
4. Rank by where the work happened, not by which session is longest. [Summing per session gets this wrong]({{ site.baseurl }}/2026/10/08/summing-bm25-per-session-let-the-longest-sessions-win.html).
5. Keep working when a VM is off or deleted. memex asks each machine live, so a destroyed VM takes its history with it. I copy history home instead. The cost is sync lag and duplicated storage.
6. Redact secrets in result snippets, [including the half you didn't show]({{ site.baseurl }}/2026/10/08/scrubbing-only-the-visible-snippet-leaks-half-a-secret.html).
7. Taking over a session running somewhere else has to stop [every process on it]({{ site.baseurl }}/2026/10/08/two-processes-can-run-the-same-ai-coding-session.html) first.

Plain "search your transcripts" is mostly solved. Liveness, jumping to the right pane, and surviving deleted machines are where the tools still differ.
