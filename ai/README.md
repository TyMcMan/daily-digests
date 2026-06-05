# AI Daily Digest — generation rules

This section is generated nightly by a scheduled agent. Structure:

```
index.html        iframe viewer shell (topbar + prev/next/Latest) — never edited
days.js           window.DIGEST_DAYS = ["YYYY-MM-DD", ...] — one entry appended per run
template.html     canonical digest-page design with {{TOKENS}} — copied, never redesigned
digests/          one self-contained page per day — written once, never edited
sources.md        the fixed source list to monitor — do not re-derive
seen-links.log    every URL ever reported — dedup store
```

## Rules for the generating agent

1. Copy `template.html`, replace the `{{TOKENS}}`, save as `digests/YYYY-MM-DD.html`.
2. Append the date to `DIGEST_DAYS` in `days.js` (ascending order, valid JS).
3. Append all reported URLs to `seen-links.log`.
4. Never edit `index.html`, `template.html`, or any existing digest page.
5. Stay inside `ai/` — never touch the repo root or the `photonics/` section.

## Content contract (same discipline as photonics/)

- **Every link must come from a page actually fetched or a search result received
  in this run. Never construct a URL from memory. `href="#"` is forbidden.**
- A sparse digest is a correct digest — empty sections say so; never pad.
- URLs in `seen-links.log` are excluded; a developing story may reappear only
  with an "update" tag and genuinely new substance.
- Max 25 items total. Every item dated within the last 24h or tagged catch-up.
