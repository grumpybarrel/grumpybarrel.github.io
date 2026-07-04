# Grumpy Barrel GitHub Pages — Compact Claude Code Build Prompt

Build a new static GitHub Pages portfolio website for **Grumpy Barrel**, a small Singapore-based video production / videography studio.

Goal: a simple, fast, video-first portfolio that immediately shows the work, builds credibility through recognisable brands, and makes it easy to contact the studio. Keep the site clean and low-maintenance. Do not build a complicated agency website.

## Brand direction

Use this tone: direct, grounded, warm, craft-focused, slightly characterful, not corporate and not over-written.

Primary tagline:

> Small films with grit, heart, and a clean finish.

Design style:
- Dark/moody cinematic aesthetic.
- Minimal navigation: **Work**, **About**, **Contact**.
- Large video thumbnails/embeds.
- Strong typography, restrained layout, no flashy animations.
- Use system fonts, responsive layout, and accessible contrast.
- Let the videos be the visual focus.

## Contact / source details

Use these details:
- Email: `scott@grumpybarrel.com`
- Phone: `+65 9639 0303`
- Address: `33 Ubi Avenue 3, Vertex, #05-49, Singapore 408868`
- Vimeo profile: `https://vimeo.com/scotttes`
- Custom domain: `grumpybarrel.com`

Do not copy the old Wix layout. Only use the old Wix site as content reference. Write better, cleaner copy.

## Technical stack

Create a Jekyll-based GitHub Pages repo.

Required infrastructure:
- `_config.yml`
- `Gemfile`
- `.gitignore`
- `CNAME`
- `.github/workflows/deploy.yml`
- `_layouts/default.html`
- `_layouts/page.html`
- `_layouts/project.html`
- `_includes/elements/button.html`
- `_includes/elements/figure.html`
- `_includes/elements/video-embed.html`
- `pages/index.md`
- `pages/projects.html`
- `pages/about.md`
- `pages/contact.md`
- `pages/404.html`
- `assets/css/main.css`
- Placeholder dirs: `assets/images/`, `assets/projects/`
- `_projects/` collection with project markdown files listed below
- `README.md`

Use Jekyll 4.3, GitHub Actions deployment, and GitHub Pages-compatible plugins: `jekyll-feed`, `jekyll-seo-tag`, `jekyll-sitemap`.

`_config.yml` requirements:
- title: `Grumpy Barrel`
- description: use the primary tagline
- baseurl: empty string
- url: `https://grumpybarrel.com`
- collection `projects` with `output: true`, permalink `/projects/:name/`
- default layout `project` for projects
- kramdown hard_wrap true
- exclude standard build/dev files

GitHub Actions workflow:
- trigger on push to `main` and `workflow_dispatch`
- permissions: contents read, pages write, id-token write
- concurrency group `pages`, cancel-in-progress false
- build using Ruby 3.3, bundler cache, configure-pages, Jekyll build, upload-pages-artifact
- deploy to `github-pages`
- use current actions: checkout v4, ruby/setup-ruby v1, configure-pages v5, upload-pages-artifact v3, deploy-pages v4

`CNAME` should contain only:

```txt
grumpybarrel.com
```

## Site structure and behaviour

### Homepage `/`

Create a video-first landing page with:
1. Hero section: brand name, tagline, short intro, CTA buttons to Work and Contact.
2. Featured work: show featured project cards first, with large thumbnails and project metadata.
3. Client/brand proof strip: simple text/logo-style list of recognisable clients/brands from the project data.
4. Services summary: Commercials, Brand Films, Event Recaps, Fashion/Beauty, Social Video, Documentary/Story Work.
5. Short about teaser with link to About.
6. Contact CTA.

### Work page `/projects/`

Show all projects in a responsive grid. Each card should include thumbnail, title, client/brand, category, short description, and link to project page.

Add simple category tags visually, but no JS filtering is needed.

### Project page

Each project page should show:
- Back link to Work
- Title
- Client/brand
- Date if available
- Category/tags
- Description
- Responsive Vimeo embed if `video_embed` exists
- Optional thumbnail image fallback
- Body content
- CTA to contact / view more work

### About page

Write concise copy around:
- Grumpy Barrel is a small video production studio in Singapore.
- The studio helps brands, events, and people turn ideas into clean, memorable visual stories.
- Tone should mention honesty, grit, attention to detail, collaboration, and heart.
- Avoid pretending to be a large agency.

### Contact page

Show email, phone, address, Vimeo link, and placeholder Instagram link. Do not build a backend form. Use a simple mailto CTA.

### 404

Simple, branded, with link home and Work.

## Project data to seed

Create one markdown file per project in `_projects/`. Use filenames shown below. Use this front matter schema:

```yaml
---
title: "..."
description: "..."
client: "..."
date: YYYY-MM-DD # omit or use approximate year if exact date unknown
category: "..."
tags: ["...", "..."]
image: /assets/projects/<slug>/thumb.jpg
video_embed: "https://player.vimeo.com/video/<ID>"
featured: true/false
---
```

Use clear placeholder descriptions. Do not claim awards or details not provided.

Seed projects:

1. `xenia-sk-ii.md`
   - Title: `Xenia - SK-II`
   - Client: `SK-II / Xenia`
   - Category: `Beauty / Fashion`
   - Vimeo ID: `1112228168`
   - Featured: true

2. `xenia-bvlgari.md`
   - Title: `Xenia - Bvlgari`
   - Client: `Bvlgari / Xenia`
   - Category: `Beauty / Fashion`
   - Vimeo ID: `1112263173`
   - Featured: true

3. `singtel-lights-out.md`
   - Title: `Singtel - Lights Out`
   - Client: `Singtel`
   - Category: `Commercial / Brand Film`
   - Vimeo ID: `1033460387`
   - Featured: true

4. `singtel-cny.md`
   - Title: `Singtel - CNY`
   - Client: `Singtel`
   - Category: `Commercial / Festive Campaign`
   - Vimeo ID: `1050008238`
   - Featured: true

5. `kfc-mala-goldspice.md`
   - Title: `KFC Mala Goldspice`
   - Client: `KFC`
   - Category: `Food / Commercial`
   - Vimeo ID: `1002610496`
   - Featured: true

6. `sentosa-gf24-grillsharing.md`
   - Title: `Sentosa - GF24 GrillSharing`
   - Client: `Sentosa`
   - Category: `Event / Destination / Food`
   - Vimeo ID: `1112233251`
   - Featured: true

7. `gastrobeats-asahi-tfoe.md`
   - Title: `Gastrobeats - Asahi TFOE`
   - Client: `Gastrobeats / Asahi`
   - Category: `Event / Beverage / Recap`
   - Vimeo ID: `1112235896`
   - Featured: true

8. `ck-spring-2023.md`
   - Title: `C&K Spring 2023`
   - Client: `Charles & Keith`
   - Category: `Fashion / Internal Video`
   - Vimeo ID: `754600739`
   - Featured: false

Add a few generic placeholder projects only if useful, but keep real Vimeo-backed projects first.

## CSS requirements

Create `assets/css/main.css` with:
- CSS reset and `box-sizing: border-box`
- dark background around `#111`
- light text around `#e8e8e8`
- muted text color
- warm accent color
- max-width around 1100px
- responsive nav
- project card grid: 3 columns on wide screens, 2 on tablets, 1 on mobile
- responsive 16:9 video embeds
- image/figure styles with size variants: `figure-xs`, `figure-sm`, `figure-md`, `figure-lg`
- button/external-link styles
- footer with subtle border-top
- no dependency on external CSS frameworks

## README

Include:
- what the site is
- local dev instructions
- GitHub Pages deployment setup
- custom domain DNS notes for GitHub Pages
- how to add a new project
- project structure overview

## Build behaviour

Implement the full repo in one pass. Do not skip files. Keep code simple and readable. Do not print every file in full unless necessary; summarize what was created and mention any commands I should run to test locally.
