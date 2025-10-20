# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal cybersecurity blog built with **Jekyll** using the **Chirpy theme** (`jekyll-theme-chirpy`). The site is hosted on GitHub Pages at `https://kyberzo.github.io` and automatically deploys when changes are pushed to the `main` or `master` branch.

## Common Development Commands

All commands should be run from the repository root directory.

### Setup
```bash
bundle install  # Install dependencies from Gemfile
```

### Local Development
```bash
bash tools/run.sh                    # Run Jekyll server locally at http://127.0.0.1:4000
bash tools/run.sh -H 0.0.0.0         # Bind to all interfaces
bash tools/run.sh -p                 # Run in production mode (equivalent to JEKYLL_ENV=production)
```

### Build & Test
```bash
bash tools/test.sh                   # Build site and run html-proofer (validates internal links)
bash tools/test.sh -c _config.yml    # Build with specific config file
JEKYLL_ENV=production bundle exec jekyll b  # Direct build in production mode
```

### Direct Jekyll Commands
```bash
bundle exec jekyll serve             # Serve locally with live reload
bundle exec jekyll build             # Build static site to _site/
```

## Project Structure

### Key Directories
- **`_posts/`** - Blog posts in Markdown format (organized by year subdirectories)
- **`_tabs/`** - Static pages: `about.md`, `archives.md`, `categories.md`, `tags.md`
- **`_layouts/`** - Custom HTML layouts: `home.html`, `post.html` (extends Chirpy theme)
- **`_includes/`** - Reusable HTML snippets: `embed/`, `pageviews/`
- **`_plugins/`** - Jekyll plugins (Ruby): `posts-lastmod-hook.rb`
- **`_data/`** - YAML data files: `contact.yml`, `share.yml`
- **`assets/`** - Static assets (avatar, images, CSS, JS)
- **`tools/`** - Development scripts: `run.sh`, `test.sh`

### Configuration
- **`_config.yml`** - Main Jekyll configuration (site title, theme, build options, analytics)
- **`Gemfile`** - Ruby dependencies (Jekyll, Chirpy theme, html-proofer)
- **`.github/workflows/pages-deploy.yml`** - Automated build and deploy workflow for GitHub Pages

## Post Front Matter Structure

Blog posts are YAML-formatted Markdown files in `_posts/`. Required and common fields:

```yaml
---
title: Post Title
description: Brief description for SEO
date: YYYY-MM-DD HH:MM:SS +TZINFO
categories: [Category1, Category2]  # Used for /categories/:name/ URLs
tags: [tag1, tag2, tag3]             # Used for /tags/:name/ URLs
pin: true                            # (optional) Pin post to top
comments: true                       # (optional) Enable post comments
toc: true                            # (optional) Show table of contents
---
```

Categories follow a hierarchical naming pattern (e.g., `[Analysis, Legacy]`). Posts use the permalink pattern `/posts/:title/` as defined in `_config.yml`.

## Automatic Features

### Last Modified Date
The `posts-lastmod-hook.rb` plugin automatically sets `last_modified_at` for posts that have been committed multiple times by querying git history. No manual action required.

### Analytics
GoatCounter analytics is configured in `_config.yml` with ID `kyberzo`. Site is set to dark theme (`theme_mode: dark`).

### PWA
Progressive Web App is enabled with offline caching support.

## Build & Deployment

**GitHub Actions Workflow** (`.github/workflows/pages-deploy.yml`):
1. Triggers on push to `main` or `master` (ignores .gitignore, README.md, LICENSE)
2. Builds Jekyll site with Ruby 3.3
3. Runs html-proofer to validate all internal links
4. Automatically deploys to GitHub Pages if all checks pass

**Note:** Builds ignore external links, localhost, and 127.0.0.1 URLs in html-proofer validation.

## Development Notes

- **Ruby Version:** 3.3 (as specified in workflow and development)
- **Theme Configuration:** Most customizations happen in `_config.yml`; Chirpy provides base layouts and styling
- **Timezone:** Europe/Helsinki (set in `_config.yml`)
- **Baseurl:** Empty string (site serves from repository root)
- **Code Syntax Highlighting:** Rouge with block line numbers enabled
- **HTML Compression:** Enabled in production builds

## Content Guidelines

- Blog posts go in `_posts/YYYY/YYYY-MM-DD-post-title.md`
- Static pages go in `_tabs/` (e.g., about, archives, categories, tags pages)
- Both posts and tabs use Markdown with Jekyll Liquid template support
- Post titles are automatically converted to URL slugs; use hyphens for multi-word titles
