---
title: "relay.damus.io banned my IP after about 6 quick writes"
tags: [nostr]
---
Publishing chunked events to relay.damus.io, one per second. After roughly six:

```
banned: too many rate-limit violations
```

Still banned 23 minutes later. Reads kept working, writes did not.

Rules I use now for every relay:

- one websocket per relay per command
- at least 3 s between publishes
- on `rate-limited:`, wait 30 s and retry once, then give up on that relay for this run

Damus is still in my list, but last and not as a default for writes.
