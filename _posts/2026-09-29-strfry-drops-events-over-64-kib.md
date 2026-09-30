---
title: "strfry drops events over 64 KiB, whatever NIP-11 says"
tags: [nostr]
---
I was storing encrypted blobs on Nostr relays as kind 30078 events. nos.lol says `max_message_length: 131072` in its NIP-11 document. An 87 KB event still bounced:

```
invalid: event too large: 87857
```

Same on nostr.mom and purplerelay.com, all strfry, all advertising 131072. My guess: strfry has a separate max event size (64 KiB by default), and NIP-11 reports the websocket message limit instead. So the advertised number is not the one that matters.

What I do now: split blobs into 30000-byte chunks. Base64 makes that 40000 characters, NIP-44 pads it to 40960, and the whole event lands at 55099 bytes. Fits everywhere I tried. A 200 KB blob becomes 7 chunks plus a small head event with the count and a sha256.

Not every strfry relay rejected it (nostr.oxtr.dev took 88 KB), so it is a config default, not a hard rule.
