---
title: "CryptPad quietly adds a salt to your username"
tags: [cryptpad]
---
If you log in to CryptPad from your own code, check `/customize/application_config.js` first. Instances can set `AppConfig.loginSalt`, and CryptPad appends it to the username before the scrypt step. Both instances I used set one. Skip it and your derived credentials won't match what the web client would compute.
