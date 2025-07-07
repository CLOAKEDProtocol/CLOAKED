# CLOAKED Protocol Documentation Repository

**Complete GitBook documentation with cyber-themed styling**

## Quick Setup for New Repository

### 1. Create New Repository
1. **Create a new repository** on GitHub (e.g., `cloaked-protocol-docs`)
2. **Copy all files** from this `docs/` folder to the new repository root
3. **Rename `DOCS_README.md`** to `README.md` (replace the existing one)

### 2. Deploy to GitHub Pages
1. **Push to GitHub:**
   ```bash
   git add .
   git commit -m "Initial GitBook documentation"
   git push origin main
   ```

2. **Enable GitHub Pages:**
   - Go to repository Settings → Pages
   - Select "GitHub Actions" as source
   - The workflow will automatically deploy your docs

3. **Live at:** `https://yourusername.github.io/repository-name/`

## Features

✅ **Complete cyber-themed styling**  
✅ **Responsive design**  
✅ **Automatic deployment**  
✅ **Custom animations and effects**  
✅ **Mobile-optimized**  

## 📁 Repository Structure

```
repository-root/
├── .github/workflows/    # Automatic deployment
├── introduction/         # Protocol overview
├── technical/           # Technical docs
├── economics/           # Tokenomics
├── governance/          # Roadmap
├── resources/           # Additional resources
├── styles/              # Custom cyber CSS
├── book.json           # GitBook configuration
├── SUMMARY.md          # Navigation structure
└── README.md           # Homepage content
```

## Local Development

```bash
# Install dependencies
npm install

# Serve locally (http://localhost:4000)
npm run serve

# Build for production
npm run build
```

## Custom Domain (Optional)

1. **Update `.github/workflows/deploy.yml`:**
   ```yaml
   cname: docs.cloakedprotocol.com
   ```

2. **Configure DNS:**
   - Add CNAME record pointing to `yourusername.github.io`

## 📝 Content Updates

- **Edit any `.md` file** to update content
- **Modify `SUMMARY.md`** to change navigation
- **Update `styles/website.css`** for styling changes
- **Push changes** → automatic deployment

---

**ANONYMOUS. SECURED. CLOAKED.** 