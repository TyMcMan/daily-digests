# Daily Digests

Umbrella site for nightly research digests, served via GitHub Pages:
**https://tymcman.github.io/daily-digests/**

```
index.html    landing page — pick a digest (status lamps show freshness)
photonics/    Photonics Daily — generated nightly at 3 AM by a scheduled
              Claude Code routine; rules and structure in photonics/README.md
ai/           AI Daily Digest — iframe viewer (index.html) + digests/ pages,
              manifest in days.js (window.DIGEST_DAYS)
```

Each section is self-contained and keeps its own manifest. The landing page
reads both manifests (`photonics/manifest.js`, `ai/days.js`) at view time —
generators only ever **add** files inside their own section; nothing at the
root needs editing.

**Rule for generating agents:** stay inside your own subdirectory. Never touch
`index.html` at the root or anything in the other section.
