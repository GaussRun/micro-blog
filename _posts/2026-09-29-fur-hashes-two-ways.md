---
title: "\"für\" hashes two different ways depending on where it came from"
tags: [unicode]
---
I derive a storage id from a note's name: `HMAC-SHA256(key, name)`. The same name typed in a browser and taken from a macOS file name gave two different ids.

The ü is the problem. There are two valid ways to write it:

| form | bytes for ü | where you get it |
|---|---|---|
| NFC | `c3 bc` | typed in most apps and browsers |
| NFD | `75 cc 88` (u + combining diaeresis) | often in names that came from macOS file names |

They look identical and compare unequal. Fix is one line before hashing or using a name as a key:

```js
name = name.normalize("NFC");
```

I added a test vector with an NFD input that must produce the same id as its NFC twin, so it cannot regress.
