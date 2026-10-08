---
title: "Scrubbing only the visible snippet leaks half a secret"
tags: [security, search]
---
Search results show a short window of text around the match, with secrets redacted. I only scanned that window. When the window edge cut through an API key, the visible half matched no pattern and was shown as is.

Fix: scan a wider region extended to whole words, redact that, then cut the window out of the redacted text. Same treatment for titles and for the text sent to the LLM reranker, which I had also missed.
