# SEO Content Architect Blog

Hugo source for the [SEO Content Architect]([https://content-architect.ns5.club](https://diflowrin.com/seo-content-architect/)) blog — guides on AI content creation, WordPress automation, and social media repurposing.

**Live site:** https://diflowrin.github.io/content-architect-blog/

## Stack

- [Hugo](https://gohugo.io/) (extended) 
- Deployed automatically to GitHub Pages via GitHub Actions on every push to `main`

## Local development

```bash
hugo server -D    # live preview at http://localhost:1313
hugo --gc --minify    # production build into ./public
```

## Adding a post

Create `content/posts/my-post-slug.md` with front matter:

```yaml
---
title: "Post Title"
date: 2026-07-11T09:00:00+03:00
description: "Meta description for SEO."
tags: ["Tag1", "Tag2"]
---
```

Links between posts: `[text](other-post-slug.md)` — Hugo resolves them to permalinks at build time.

The `description` is not optional: it feeds `<meta name="description">`, `og:description`, and
`twitter:description` at once. Aim for 150–160 characters — Bing Webmaster Tools flags anything
shorter, and anything left empty falls back to the site description, which then shows up as a
duplicate across pages.

## Adding a tag

Every tag needs `content/tags/<slug>/_index.md`, otherwise its archive page inherits the site
description and Bing reports a duplicate:

```yaml
---
title: "Tag Name"
description: "What this archive collects, in 150-160 characters."
---
```

The slug is the tag name lowercased with spaces turned into hyphens (`Koala AI` → `koala-ai`).
A tag page with front matter only stays `noindex, follow` — deliberately, since a bare list of
links is a thin page. Add body text below the front matter (see `content/tags/automation/`) when
the archive is worth indexing on its own.

## SEO check before pushing

```bash
hugo --gc --minify --cleanDestinationDir
```

Then confirm every built page carries a unique 150–160 character description and that
`meta`/`og`/`twitter` agree — the three come from the same front matter field, so a mismatch means
a page is falling back to the site default.
