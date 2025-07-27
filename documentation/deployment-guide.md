---
layout: default
title: Deployment Guide
excerpt: Complete guide for deploying Jekyll sites to GitHub Pages, including custom domains, HTTPS, and automated workflows.
---

# Jekyll Deployment Guide

Learn how to deploy your Jekyll site to GitHub Pages and configure advanced features.

## Deployment Methods

### Method 1: Direct Push (Recommended for Beginners)

1. **Create Repository**: Create a new GitHub repository
2. **Push Code**: Push your Jekyll site to the `main` branch
3. **Enable Pages**: Go to Settings > Pages, select "Deploy from a branch"
4. **Select Branch**: Choose `main` branch and `/ (root)` folder

### Method 2: GitHub Actions (Advanced)

For more control over the build process:

```yaml
# .github/workflows/deploy.yml
name: Deploy Jekyll Site

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    
    - name: Setup Ruby
      uses: ruby/setup-ruby@v1
      with:
        ruby-version: 3.2
        bundler-cache: true
    
    - name: Build site
      run: bundle exec jekyll build
    
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./_site
```

## Custom Domains

### Setup Process

1. **Add CNAME File**: Create a `CNAME` file in your repository root:
   ```
   yourdomain.com
   ```

2. **Configure DNS**: Add these DNS records:
   ```
   Type: A
   Name: @
   Value: 185.199.108.153
          185.199.109.153
          185.199.110.153
          185.199.111.153
   
   Type: CNAME
   Name: www
   Value: yourusername.github.io
   ```

3. **Verify in GitHub**: Go to Settings > Pages and verify your domain

### HTTPS Configuration

GitHub Pages automatically provides HTTPS for custom domains:

- **Free SSL certificates** via Let's Encrypt
- **Automatic renewal** handled by GitHub
- **Force HTTPS** option in repository settings

## Build Configuration

### Optimizing Build Performance

```yaml
# _config.yml optimizations
exclude:
  - Gemfile
  - Gemfile.lock
  - node_modules/
  - vendor/
  - .sass-cache/
  - .jekyll-cache/

plugins:
  - jekyll-sitemap    # SEO
  - jekyll-feed       # RSS
  - jekyll-seo-tag    # Meta tags

# Sass configuration
sass:
  style: compressed
  sass_dir: _sass

# Permalink structure
permalink: /:categories/:year/:month/:day/:title/
```

## Environment Variables

### Development vs Production

```yaml
# _config.yml
url: "https://yoursite.com"
baseurl: ""

# _config.dev.yml (for local development)
url: "http://localhost:4000"
baseurl: ""
```

Local development command:
```bash
bundle exec jekyll serve --config _config.yml,_config.dev.yml
```

## Troubleshooting

### Common Issues

**Build Failures**:
- Check Gemfile compatibility with GitHub Pages
- Verify plugin support
- Review error messages in Actions tab

**CSS/JS Not Loading**:
- Check `baseurl` configuration
- Verify asset paths use `{{ "/assets/style.css" | relative_url }}`

**Slow Build Times**:
- Exclude unnecessary files
- Optimize images
- Use incremental builds locally: `--incremental`

### Debugging Tools

```bash
# Verbose build output
bundle exec jekyll build --verbose

# Check configuration
bundle exec jekyll build --dry-run

# Profile build performance
bundle exec jekyll build --profile
```

## Performance Optimization

### Image Optimization

- Use WebP format when possible
- Compress images before uploading
- Consider lazy loading for large galleries

### Caching Strategy

```yaml
# _config.yml
plugins:
  - jekyll-sitemap
  - jekyll-feed

# Enable caching
incremental: true
```

### CDN Integration

For static assets, consider using a CDN:

```html
<!-- Example: Using a CDN for common libraries -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/prismjs@1.29.0/themes/prism.min.css">
```

---

*This deployment guide showcases Jekyll's flexibility in organizing documentation while maintaining clean, hierarchical URLs.*