---
layout: default
title: Getting Started with Jekyll
excerpt: A comprehensive guide to setting up Jekyll for static site development and deployment on GitHub Pages.
---

# Getting Started with Jekyll

This guide covers the essential steps for setting up Jekyll and deploying to GitHub Pages.

## Prerequisites

Before you begin, ensure you have:

- **Git** installed on your local machine
- **Ruby** version 2.5.0 or higher
- **Bundler** gem installed (`gem install bundler`)
- A **GitHub account** for deployment

## Installation Steps

### 1. Create a New Repository

```bash
# Create and navigate to your project directory
mkdir my-jekyll-site
cd my-jekyll-site

# Initialize Git repository
git init
```

### 2. Create Gemfile

```ruby
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-remote-theme"
end
```

### 3. Install Dependencies

```bash
bundle install
```

### 4. Create Basic Configuration

Create `_config.yml`:

```yaml
title: Your Site Title
description: Your site description
baseurl: ""
url: ""

remote_theme: pages-themes/minimal@v0.2.0

plugins:
  - jekyll-feed
  - jekyll-remote-theme

page_excerpts: true
```

## Directory Structure

A typical Jekyll site structure:

```
.
├── _config.yml      # Site configuration
├── _posts/          # Blog posts
├── _layouts/        # Page templates
├── _includes/       # Reusable components
├── _sass/           # Sass stylesheets
├── assets/          # CSS, JS, images
├── index.md         # Homepage
└── about.md         # About page
```

## Creating Content

### Pages

Create pages as Markdown files:

```markdown
---
layout: default
title: My Page
---

# Page Content

Your page content goes here.
```

### Posts

Create posts in `_posts/` with the naming convention `YYYY-MM-DD-title.md`:

```markdown
---
layout: default
title: "My First Post"
date: 2025-01-01 12:00:00 +0000
categories: blog
tags: [jekyll, tutorial]
---

# Post Content

Your blog post content.
```

## Local Development

```bash
# Build and serve locally
bundle exec jekyll serve

# Build only
bundle exec jekyll build

# Serve with drafts
bundle exec jekyll serve --drafts
```

## GitHub Pages Deployment

1. **Push to GitHub**: Commit and push your code to a GitHub repository
2. **Enable Pages**: Go to repository Settings > Pages
3. **Configure Source**: Select "Deploy from a branch" and choose `main`
4. **Custom Domain** (optional): Add your domain in the settings

## Next Steps

- Explore [Jekyll themes](https://jekyllthemes.io/)
- Learn about [Liquid templating](https://shopify.github.io/liquid/)
- Read the [Jekyll documentation](https://jekyllrb.com/docs/)
- Join the [Jekyll community](https://talk.jekyllrb.com/)

---

*This documentation demonstrates Jekyll's ability to organize content in subfolders while maintaining clean URLs.*