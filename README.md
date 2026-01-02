# Kai's Blog

A personal blog built with [Astro](https://astro.build/), featuring markdown support, syntax highlighting, RSS feed, and deployment to GitHub Pages.

## Features

- 🚀 Built with Astro for optimal performance
- 📝 Full Markdown/MDX support for blog posts
- 🎨 Syntax highlighting with Shiki (VS Code quality)
- 📱 Responsive design
- 📡 RSS feed for subscribers
- ⚡ Zero JavaScript by default

## Getting Started

### Prerequisites

- Node.js 18+ 
- npm

### Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev
```

The site will be available at `http://localhost:4321`

### Building for Production

```bash
npm run build
```

The built site will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## Project Structure

```
├── public/
│   ├── images/
│   │   ├── profile.jpeg            # Your profile photo
│   │   └── space.jpg               # Bruce McCandless spacewalk photo
│   └── favicon.svg
├── src/
│   ├── content/
│   │   ├── blog/                   # Blog posts (Markdown)
│   │   └── config.ts               # Content collection schema
│   ├── layouts/
│   │   ├── BaseLayout.astro        # Base HTML layout
│   │   └── BlogPost.astro          # Blog post layout
│   └── pages/
│       ├── index.astro             # Homepage (blog list)
│       ├── about.astro             # About page
│       ├── rss.xml.ts              # RSS feed
│       └── blog/[...slug].astro    # Blog post pages
├── astro.config.mjs
└── package.json
```

## Writing Blog Posts

Create new blog posts in `src/content/blog/` with the following frontmatter:

```markdown
---
title: "Your Post Title"
description: "A brief description of your post"
date: 2025-01-01
tags: ["tag1", "tag2"]
draft: false
---

Your content here...
```

### Supported Markdown Features

- Headers, paragraphs, lists
- Code blocks with syntax highlighting
- Images
- Blockquotes
- Tables
- Links

## Deployment

The site automatically deploys to GitHub Pages when you push to the `master` branch.

### GitHub Pages Setup

1. Go to your repository Settings → Pages
2. Under "Build and deployment", select "GitHub Actions"
3. Push to `master` and the site will deploy automatically

## RSS Feed

The RSS feed is available at `/rss.xml`. Readers can subscribe to get updates when new posts are published.

## Customization

- **Colors**: Edit CSS variables in `src/layouts/BaseLayout.astro`
- **Fonts**: Update Google Fonts links in `BaseLayout.astro`
- **Site metadata**: Update `astro.config.mjs` and page titles

