---
title: "Searching for \"ats\" matched every prompt with \"at\""
tags: [search]
---
The Porter stemmer turns `ats` into `at`. So a three-letter query matched half my corpus.

Fix: if a word's stem is one or two letters, match the word as typed instead of the stem.
