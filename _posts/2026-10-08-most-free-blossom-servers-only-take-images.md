---
title: "Most free Blossom servers only take images"
tags: [nostr, blossom]
---
I uploaded 50 KB of random bytes as `application/octet-stream` to 22 Blossom servers. 7 took it: nostr.download, blossom.ditto.pub, cdn.hzrd149.com, blossom.yakihonne.com, files.sovbit.host, blossom.nmail.li, blossom.jumble.social.

7 refused anything that isn't media (415 or 400). The rest needed payment, an account, a whitelist, or were gone.

I didn't relabel the bytes as `image/png` to get past the media-only ones. People offer free image hosting, not free storage.

None of them state how long they keep data. NIP-96 `file_expiration` is `[0,0]` everywhere I looked.
