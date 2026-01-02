---
title: "Building a Blog with Astro"
description: "A walkthrough of how I built this blog using Astro, including markdown support, code highlighting, and deployment to GitHub Pages."
date: 2025-01-02
tags: ["tutorial", "astro", "web"]
---

I recently rebuilt my personal site using [Astro](https://astro.build/), and I wanted to share the experience. Astro has become my go-to for content-focused sites, and for good reason.

## Why Astro?

Astro offers several compelling features for blogs:

- **Zero JavaScript by default** — Your pages ship as pure HTML unless you need interactivity
- **Built-in Markdown support** — With excellent code highlighting via Shiki
- **Content Collections** — Type-safe content management
- **Island Architecture** — Add interactivity only where needed

## Project Structure

Here's how I organized my blog:

```
src/
├── content/
│   ├── blog/
│   │   ├── hello-world.md
│   │   └── building-with-astro.md
│   └── config.ts
├── layouts/
│   ├── BaseLayout.astro
│   └── BlogPost.astro
├── pages/
│   ├── index.astro
│   └── blog/
│       └── [...slug].astro
└── styles/
    └── global.css
```

## Content Collections

Astro's content collections provide type safety for your content. Here's my configuration:

```typescript
import { defineCollection, z } from 'astro:content';

const blog = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    description: z.string(),
    date: z.date(),
    draft: z.boolean().optional().default(false),
    tags: z.array(z.string()).optional().default([]),
  }),
});

export const collections = { blog };
```

This gives you autocompletion and type checking for your frontmatter.

## Code Highlighting

Astro uses [Shiki](https://shiki.matsu.io/) for syntax highlighting. The configuration is simple:

```javascript
// astro.config.mjs
export default defineConfig({
  markdown: {
    shikiConfig: {
      theme: 'github-dark',
      wrap: true
    }
  }
});
```

The result is beautiful, VS Code-quality highlighting without shipping any JavaScript.

## Deploying to GitHub Pages

Deploying is straightforward with GitHub Actions. Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
    steps:
      - uses: actions/deploy-pages@v4
```

## Final Thoughts

Astro has been a joy to work with. The focus on content and performance aligns perfectly with what a blog needs. If you're building a content-focused site, I highly recommend giving it a try.

> "The best tool is the one that gets out of your way and lets you focus on what matters."

Happy building!

