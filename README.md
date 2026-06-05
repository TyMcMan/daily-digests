# Photonics Daily

A static digest site generated nightly by a scheduled Claude Code agent. Open
`index.html` (or the GitHub Pages URL) — it redirects to the newest digest.
Navigate between days with the ← → arrows in the header.

## How it works

```
index.html        redirects to the newest date in manifest.js — never edited
manifest.js       window.DIGEST_DATES = ["YYYY-MM-DD", ...] — one line appended per run
template.html     canonical page design — copied, never redesigned
YYYY-MM-DD.html   one self-contained digest per day — written once, never edited
seen-links.log    every URL ever reported, one per line — dedup store
photonics-sources.md   the vetted source list the agent monitors
```

Navigation is computed **at view time** from `manifest.js`, so yesterday's page
gains a working → arrow the moment today's date is appended — no old file is
ever touched.

## Rules for the generating agent

1. Copy `template.html`, replace the `{{TOKENS}}`, save as `YYYY-MM-DD.html`.
2. Append the date to `DIGEST_DATES` in `manifest.js` (keep ascending order).
3. Append all reported URLs to `seen-links.log`.
4. Never edit any existing `*.html` page, `index.html`, or `template.html`.
5. Commit and push: `digest: YYYY-MM-DD (<n> items)`.

### Item markup

```html
<article class="item">
  <h3><a href="https://...">Title</a><span class="badge">update</span></h3>
  <p>Two–three sentence summary. <em>Why it matters:</em> one clause.</p>
  <div class="meta">source &middot; YYYY-MM-DD</div>
</article>
```

- Badge element only for `update` / `catch-up` items; omit it otherwise.
- Empty section body: `<p class="empty">Nothing new today.</p>`
- TL;DR entries: `<li><a href="#section-id">one line</a></li>`

## Recovery

- **manifest.js corrupted:** rebuild from disk —
  `ls 20*.html | sed 's/\.html//' | sort` and re-wrap as the array. Or `git revert`.
- **Anything else:** every run is one commit; `git log` is the audit trail.
