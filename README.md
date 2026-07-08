# Weekly News Digest

A weekly digest of US, world, tech, Arkansas, and pop-culture news.

**Site:** https://dillonkh.github.io/news-digest/

This is a personal project hosted on GitHub Pages purely to take advantage
of free static hosting. It's not intended for outside contributions — no
issues or PRs, please.

## Running locally

Requires Ruby (version pinned in `.ruby-version`) and Bundler.

```bash
bundle install
bundle exec jekyll serve --baseurl ""
# http://localhost:4000
```

**macOS troubleshooting:** if `bundle install` fails building `eventmachine`
with `'iostream' file not found`, your CommandLineTools clang isn't finding
libc++ headers. Fix by adding this to your shell profile, then retry:

```bash
export CPATH="$(xcrun --show-sdk-path)/usr/include/c++/v1"
```

## Adding a weekly digest

Create `_digests/YYYY-MM-DD.html`, where the filename date is the **window end
date** (the later date in the range). The filename — not the `date` field —
determines archive sort order, so keep it in strict `YYYY-MM-DD` form.

```html
---
title: "Weekly News Digest: <range>"
range: "<range>"                 # e.g. "June 28 – July 5, 2026"
date: 2026-07-06                 # compile date; display only (footer line)
bias_score: -1                   # integer -7..7; drives the gauge marker
bias_label: "slightly left of center"
bias_blurb: "One-sentence TL;DR of the rating."
bias_detail: "Full 2-3 sentence justification."
---

<p><span class="lead">Lead sentence...</span> ...</p>
<hr>
<h2>🏛️ US Politics &amp; Policy</h2>
<div class="item">
  <h3>Headline</h3>
  <p>Content...</p>
  <p class="src">Source A, Source B</p>
</div>
```

No `<head>`, `<style>`, or `<html>` — the layout supplies all of that.

The bias rating is **not** written in the body. Put it in the front-matter
`bias_*` fields above; the layout renders the ⚖️ heading, the big score, the
blue→red gauge, and the text.

### Section headers use emoji

| Section                          | Header                                   |
|----------------------------------|------------------------------------------|
| US Politics & Policy             | `<h2>🏛️ US Politics &amp; Policy</h2>`   |
| World News                       | `<h2>🌍 World News</h2>`                  |
| Tech News                        | `<h2>💻 Tech News</h2>`                   |
| Arkansas                         | `<h2>🐗 Arkansas</h2>`                    |
| Pop Culture                      | `<h2>🎬 Pop Culture</h2>`                 |
| Sources                          | `<h2>🔗 Sources</h2>`                     |
| This Week in Arkansas History    | `<h3>📚 ...</h3>` (inside `.history`)     |

The ⚖️ bias heading is added by the layout — don't write it yourself.

### Shared CSS classes (body content)

| Class      | Purpose                                     |
|------------|---------------------------------------------|
| `.lead`    | Bold lead clause inside a paragraph         |
| `.item`    | A single news-item block                    |
| `.src`     | Source attribution line                     |
| `.history` | "This Week in Arkansas History" callout     |
| `.sources` | Sources link-list wrapper                   |

`.biasbox` and the gauge markup are rendered by the layout from front matter,
not authored in the body.

## Styling

All styling lives in `assets/css/digest.css` (warm minimalist serif theme).
It uses CSS custom properties in `:root`, so the whole palette retunes from
that block. `_layouts/digest.html` owns the page structure.
