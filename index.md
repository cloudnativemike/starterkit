---
layout: default
title: Breaking News from the Cloud
---

## Latest Headlines

<p style="margin-bottom: 20px;"><a href="{{ '/tags/' | relative_url }}">Browse all articles by tags</a></p>

{% for post in site.posts %}
### [{{ post.title }}]({{ post.url }})
*{{ post.date | date: "%B %d, %Y" }}* | **{{ post.categories | join: ", " | capitalize }}**

{% assign excerpt_lines = post.excerpt | strip_html | split: "
" %}
{% assign excerpt_without_title = excerpt_lines | shift | join: "
" %}
{{ excerpt_without_title | truncate: 200, "" }} [Read more →]({{ post.url }})

---
{% endfor %}

## Educational Resources

This site demonstrates Jekyll's capabilities for:
- **Static site generation** with Markdown content
- **GitHub Pages deployment** with automated workflows  
- **Responsive design** using minimal themes
- **SEO optimization** with structured data
- **Blog functionality** with posts and categories

### Quick Start Guide
1. Fork this repository
2. Edit `_config.yml` with your details
3. Add posts to `_posts/` directory
4. Push to GitHub - site deploys automatically!

**Related Reading:**
- {% post_url 2025-01-08-github-pages-hosting-revolution %}
- {% post_url 2025-01-15-jekyll-revolutionizes-static-sites %}

---

## About The Cloud Times

The Cloud Times showcases modern web development practices using Jekyll and GitHub Pages. This educational demo site illustrates:

- **Content management** through Markdown files
- **Version control** integration with Git
- **Automated deployment** via GitHub Actions
- **Professional hosting** at zero cost
- **Modern web standards** and best practices

Perfect for learning static site development, Git workflows, and cloud deployment strategies.

*Built using Jekyll, hosted on GitHub Pages*
