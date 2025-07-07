# CLOAKED Protocol GitBook Setup Guide

## Overview

This guide will help you set up and deploy the CLOAKED Protocol GitBook with custom cyber-themed styling that matches your website's aesthetic.

## Prerequisites

### Node.js and npm
```bash
# Install Node.js (version 16 or higher)
# Visit https://nodejs.org/ or use a package manager

# Verify installation
node --version
npm --version
```

### GitBook CLI
```bash
# Install GitBook CLI globally
npm install -g gitbook-cli

# Verify installation
gitbook --version
```

## Installation Steps

### 1. Install GitBook Dependencies

```bash
# Navigate to your project directory
cd path/to/your/gitbook

# Install GitBook plugins
gitbook install

# This will install the plugins specified in book.json:
# - theme-default
# - prism
# - copy-code-button
# - expandable-chapters
# - anchors
# - search-pro
# - custom-favicon
```

### 2. Create Required Directories

```bash
# Create necessary directories
mkdir -p assets
mkdir -p styles
mkdir -p introduction
mkdir -p technical
mkdir -p use-cases
mkdir -p economics
mkdir -p developers
mkdir -p governance
mkdir -p resources
```

### 3. Add Favicon (Optional)

```bash
# Copy your favicon to the assets directory
cp path/to/your/favicon.ico assets/

# Or use the website's favicon
cp public/static/favicons/favicon-32x32.png assets/favicon.ico
```

## Local Development

### 1. Start Development Server

```bash
# Serve the GitBook locally
gitbook serve

# This will:
# - Build the GitBook
# - Start a local server
# - Watch for changes and auto-reload
# - Usually available at http://localhost:4000
```

### 2. Build for Production

```bash
# Build static files
gitbook build

# This creates a _book directory with:
# - All HTML files
# - CSS and JS assets
# - Images and other static files
```

## Deployment Options

### Option 1: GitHub Pages

```bash
# 1. Create a new repository on GitHub
# 2. Add your GitBook files to the repository
# 3. Push to GitHub

git init
git add .
git commit -m "Initial GitBook setup"
git remote add origin https://github.com/yourusername/cloaked-docs.git
git push -u origin main

# 4. Enable GitHub Pages in repository settings
# 5. Select "GitHub Actions" as the source
# 6. Create .github/workflows/deploy.yml:
```

**GitHub Actions Workflow (.github/workflows/deploy.yml):**
```yaml
name: Deploy GitBook

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    
    - name: Setup Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '16'
    
    - name: Install GitBook CLI
      run: npm install -g gitbook-cli
    
    - name: Install dependencies
      run: gitbook install
    
    - name: Build GitBook
      run: gitbook build
    
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./_book
```

### Option 2: Vercel Deployment

```bash
# 1. Install Vercel CLI
npm install -g vercel

# 2. Deploy to Vercel
vercel

# 3. Follow the prompts to configure deployment
```

**Vercel Configuration (vercel.json):**
```json
{
  "version": 2,
  "builds": [
    {
      "src": "book.json",
      "use": "@vercel/static-build",
      "config": {
        "distDir": "_book"
      }
    }
  ],
  "scripts": {
    "build": "gitbook install && gitbook build"
  }
}
```

### Option 3: Netlify Deployment

```bash
# 1. Build the GitBook
gitbook build

# 2. Upload _book directory to Netlify
# 3. Or connect GitHub repository to Netlify
```

**Netlify Configuration (netlify.toml):**
```toml
[build]
  command = "gitbook install && gitbook build"
  publish = "_book"

[build.environment]
  NODE_VERSION = "16"
```

### Option 4: Custom Domain Setup

```bash
# 1. After deploying to any platform, configure custom domain
# 2. Add CNAME file to _book directory (for GitHub Pages):
echo "docs.cloakedprotocol.com" > _book/CNAME

# 3. Configure DNS settings:
# - Add CNAME record pointing to your hosting platform
# - For GitHub Pages: yourname.github.io
# - For Vercel: cname.vercel-dns.com
# - For Netlify: yoursite.netlify.app
```

## Customization Guide

### 1. Updating Content

```bash
# Edit any .md file in the structure
# The main files are:
# - README.md (homepage)
# - SUMMARY.md (navigation)
# - introduction/*.md
# - technical/*.md
# - use-cases/*.md
# - economics/*.md
# - etc.
```

### 2. Modifying Styles

```bash
# Edit styles/website.css for custom styling
# The file includes:
# - Cyber-themed color scheme
# - Custom fonts (Orbitron, Share Tech Mono)
# - Animations and effects
# - Responsive design
```

### 3. Adding New Sections

```bash
# 1. Create new markdown files
# 2. Add to SUMMARY.md navigation
# 3. Update cross-references in other files
```

### 4. Plugin Configuration

```bash
# Edit book.json to:
# - Add/remove plugins
# - Configure plugin settings
# - Update metadata
```

## Advanced Configuration

### Custom CSS Variables

```css
/* Add to styles/website.css */
:root {
  --primary-bg: #000000;
  --accent-color: #ffffff;
  --text-primary: #ffffff;
  /* Customize colors to match your brand */
}
```

### Custom JavaScript

```javascript
// Add to assets/custom.js
// Custom functionality for your GitBook
```

### Analytics Integration

```json
// Add to book.json
{
  "plugins": ["google-analytics"],
  "pluginsConfig": {
    "google-analytics": {
      "token": "YOUR_GA_TOKEN"
    }
  }
}
```

## Troubleshooting

### Common Issues

1. **Plugin Installation Fails**
   ```bash
   # Clear npm cache
   npm cache clean --force
   
   # Reinstall GitBook
   npm uninstall -g gitbook-cli
   npm install -g gitbook-cli
   ```

2. **Build Errors**
   ```bash
   # Check for markdown syntax errors
   # Verify all file paths in SUMMARY.md exist
   # Ensure proper YAML frontmatter
   ```

3. **Styling Issues**
   ```bash
   # Verify CSS syntax in styles/website.css
   # Check browser console for errors
   # Test on different devices/browsers
   ```

### Performance Optimization

```bash
# Optimize images
# Use WebP format when possible
# Compress CSS and JavaScript
# Enable CDN for faster loading
```

## Maintenance

### Regular Updates

```bash
# Update GitBook dependencies
gitbook install

# Update content regularly
# Check for broken links
# Monitor performance metrics
```

### Content Management

```bash
# Use Git for version control
# Create feature branches for major updates
# Review changes before merging
```

## Security Considerations

```bash
# Keep dependencies updated
# Use HTTPS for custom domains
# Implement proper CSP headers
# Regular security audits
```

## Final Deployment Checklist

- [ ] All content reviewed and proofread
- [ ] Navigation structure tested
- [ ] Custom styling applied and tested
- [ ] Mobile responsiveness verified
- [ ] Cross-browser compatibility checked
- [ ] Performance optimized
- [ ] SEO metadata configured
- [ ] Analytics integrated
- [ ] Custom domain configured
- [ ] SSL certificate active
- [ ] Backup and versioning in place

## Support

For issues or questions:
- Check GitBook documentation: https://docs.gitbook.com/
- Review plugin documentation
- Test locally before deploying
- Use browser developer tools for debugging

---

**Your CLOAKED Protocol GitBook is now ready to deploy!** 