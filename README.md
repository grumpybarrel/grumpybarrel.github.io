# Grumpy Barrel — grumpybarrel.com

Static portfolio site for Grumpy Barrel, a video production studio based in Singapore. Built with Jekyll and deployed via GitHub Pages.

---

## Local development

### Requirements

- Ruby 3.3+
- Bundler

### Setup

```bash
bundle install
```

### Run locally

```bash
bundle exec jekyll serve
```

The site will be available at `http://localhost:4000`.

To watch for file changes:

```bash
bundle exec jekyll serve --livereload
```

---

## Deployment

The site deploys automatically via GitHub Actions on every push to `main`. The workflow is in `.github/workflows/deploy.yml`.

### GitHub Pages setup

1. Go to **Settings → Pages** in the GitHub repo.
2. Under **Source**, select **GitHub Actions**.
3. Push to `main` — the action will build and deploy.

---

## Custom domain

The domain `grumpybarrel.com` is set in the `CNAME` file.

### DNS configuration (at your registrar)

Add the following records pointing to GitHub Pages:

| Type  | Host | Value                    |
|-------|------|--------------------------|
| A     | @    | 185.199.108.153          |
| A     | @    | 185.199.109.153          |
| A     | @    | 185.199.110.153          |
| A     | @    | 185.199.111.153          |
| CNAME | www  | grumpybarrel.github.io   |

DNS propagation can take up to 24 hours. GitHub Pages will provision HTTPS automatically once the domain resolves.

---

## Adding a new project

1. Create a new Markdown file in `_projects/`:

```bash
touch _projects/my-project-slug.md
```

2. Add front matter:

```yaml
---
title: "Project Title"
description: "One or two sentences describing the project."
client: "Client Name"
date: 2024-06-01
category: "Category / Type"
tags: ["Tag1", "Tag2"]
image: /assets/projects/my-project-slug/thumb.jpg
video_embed: "https://player.vimeo.com/video/VIMEO_ID"
featured: false
---
```

3. Add a thumbnail image at `assets/projects/my-project-slug/thumb.jpg` (recommended: 1280×720px).

4. Optionally add body content below the front matter.

5. Set `featured: true` to include the project on the homepage.

---

## Project structure

```
.
├── _config.yml              # Jekyll configuration
├── Gemfile                  # Ruby dependencies
├── CNAME                    # Custom domain
├── .github/workflows/
│   └── deploy.yml           # GitHub Actions deployment
├── _layouts/
│   ├── default.html         # Base HTML template (nav, footer)
│   ├── page.html            # Generic page wrapper
│   └── project.html         # Individual project page
├── _includes/
│   └── elements/
│       ├── button.html      # Reusable button/link component
│       ├── figure.html      # Responsive image figure
│       └── video-embed.html # Responsive Vimeo embed
├── _projects/               # Project collection (one file per project)
├── pages/
│   ├── index.md             # Homepage (/)
│   ├── projects.html        # Work page (/projects/)
│   ├── about.md             # About page (/about/)
│   ├── contact.md           # Contact page (/contact/)
│   └── 404.html             # 404 page
├── assets/
│   ├── css/
│   │   └── main.css         # All styles (no framework)
│   ├── images/              # Shared site images
│   └── projects/            # Per-project media (thumb.jpg etc.)
└── README.md
```
