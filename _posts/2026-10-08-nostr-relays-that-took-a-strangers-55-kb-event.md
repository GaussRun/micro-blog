---
title: "19 of 36 Nostr relays accepted a 55 KB event from a stranger"
tags: [nostr]
---
I tried writing one 55 KB kind 30078 event to 36 well-known relays, then read it back. 19 took it.

The 17 that refused: whitelist or members only (8), NIP-05 required (2), kind 30078 not accepted (2), plus one each of paid time ran out, AUTH needed to query, kinds not supported, message too long, and a country block.

Of the 19, these also served kind 30078 events older than 400 days, which is the closest thing to a retention signal you get: nos.lol, nostr.mom, purplerelay.com, nostr.oxtr.dev, nostr.data.haus, relay.nostr.wirednet.jp, nostr-01.yakihonne.com, relay.illuminodes.com, strfry.bonsai.com, schnorr.me.

Old events are evidence, not a promise. `created_at` is set by the author, and many relays seem to share one imported backfill ending 2024-01-03.
