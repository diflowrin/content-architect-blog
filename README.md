# SEO Content Architect Blog

Hugo source for the [SEO Content Architect](https://content-architect.ns5.club) blog — guides on AI content creation, WordPress automation, and social media repurposing.

**Live site:** https://diflowrin.github.io/content-architect-blog/

## Stack

- [Hugo](https://gohugo.io/) (extended) with the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme
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
