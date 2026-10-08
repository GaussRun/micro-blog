---
title: "Summing BM25 over a whole session let the longest sessions win"
tags: [search]
---
I search my old AI coding sessions by what I typed into them. The score was BM25 summed per session. A few long-running sessions contained every query word just by volume, so they beat the session I was looking for. Sessions still running were also sorted above relevance, which made it worse.

What I changed:

- score each prompt with BM25, then fold them with weight 1/i² for the i-th best, so repetition helps a bit and volume can't win
- extra weight when a word appears in the session's directory, repo, branch, or first prompt
- a bonus when query words appear together in one prompt
- no "must contain every word" gate; a missing word just costs what it's worth
- a running session gets a 10% boost instead of being a sort key

Labelled queries, before and after:

| queries | right session at rank 1 | MRR |
|---|---|---|
| 22 | 8 → 15 | 0.520 → 0.810 |
| 30 | 15 → 24 | 0.656 → 0.852 |
