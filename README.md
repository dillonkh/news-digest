# Weekly News Digest

A Jekyll site hosting weekly news digests, styled as a tamed-90s blog.
Hosted on GitHub Pages (project site).

## Adding a weekly digest

Create `_digests/YYYY-MM-DD.html` (date = end of the digest window):

```html
---
title: "Weekly News Digest: <range>"
range: "<range>"
date: 2026-07-06
visitors: "0001337"
---

<p><span class="lead">Lead sentence...</span> ...</p>
<hr>
<h2>&#9733; Section Name</h2>
<div class="item">
  <h3>Headline</h3>
  <p>Content...</p>
  <p class="src">Source A, Source B</p>
</div>
```

No `<head>`, `<style>`, or `<html>` — the layout supplies all of that.

### Shared CSS classes

| Class      | Purpose                              |
|------------|--------------------------------------|
| `.lead`    | Bold lead sentence                   |
| `.item`    | A single news item block             |
| `.src`     | Italic source attribution            |
| `.biasbox` | Media bias rating callout            |
| `.history` | "This Week in History" callout       |
| `.sources` | Sources link list wrapper            |

## Local preview

```bash
bundle exec jekyll serve --baseurl ""
# http://localhost:4000
```
