# Garmin Nuvi Documentation - Agent Instructions

## Project Overview

This is a MkDocs-based technical documentation site for Garmin Nuvi map update guides. The documentation provides step-by-step instructions for users updating maps on Garmin Nuvi GPS navigation devices.

**Key Purpose:** Help users understand and execute Garmin Nuvi map and software updates

**Tech Stack:** MkDocs with Material theme

**GitHub Pages:** This documentation is designed to be published via GitHub Pages

## Architecture

### Directory Structure
- `mkdocs.yml` - MkDocs configuration file (site name, theme settings, navigation structure)
- `docs/` - All markdown content
  - Root level docs: index.md, installation.md, map-update-guide.md, software-update.md, activation.md, faq.md
  - `Articles/` - Detailed guides for specific Garmin models
  - `assets/` - Images and media
  - `stylesheets/` - Custom CSS (style.css)

### Theme & Styling
- **Theme:** Material theme for MkDocs (modern, responsive design)
- **Features Enabled:** Navigation tabs, sections, dark mode toggle, search, code copy buttons
- **Color Scheme:** Blue primary, amber accent
- **Custom CSS:** `docs/stylesheets/style.css` for site-specific styling

### Content Conventions
- **Inline styling:** Uses inline HTML with gradient backgrounds, padding, and border styling for call-out boxes
- **Visual elements:** Emoji bullets (🚗, 🗺️, 💻) for section headers
- **Information blocks:** Color-coded boxes for tips, warnings, and important info
  - Light blue (#e8f4ff) with blue border for "Important" messages
  - Other gradient backgrounds for feature highlights
- **Structure:** Each guide includes headings, explanatory text, step-by-step sections, and styled info boxes

## Common Tasks

### Adding or Updating Documentation
When creating or editing markdown files in `docs/`:
1. Follow the existing heading hierarchy (H1 for page title, H2 for major sections, H3 for subsections)
2. Use inline HTML styling for information boxes (see examples in existing files)
3. Include emoji bullets for visual hierarchy (🚗, 🗺️, 💻, 🔌, etc.)
4. Add images from `docs/assets/` using relative paths: `![Alt text](./assets/image.png)`
5. Update `mkdocs.yml` navigation section if adding a new top-level page

### Building and Previewing Locally
```bash
# Install MkDocs and Material theme (one-time setup)
pip install mkdocs mkdocs-material

# Preview documentation locally (serves on http://localhost:8000)
mkdocs serve

# Build static site for deployment
mkdocs build
# Output goes to `site/` directory
```

### GitHub Pages Deployment
The documentation is published to GitHub Pages. When ready to deploy:
1. Ensure all changes are committed and pushed to the repository
2. GitHub Actions workflow (if configured) will automatically build and deploy to the `gh-pages` branch
3. Or manually run: `mkdocs gh-deploy` (pushes built site to gh-pages branch)
4. Site will be accessible at: `https://[username].github.io/garmin/` or `https://[organization].github.io/garmin/`

### GitHub Workflow Setup (Recommended)
Create `.github/workflows/deploy.yml` for automatic documentation deployment:
```yaml
name: Deploy to GitHub Pages
on:
  push:
    branches:
      - main
  pull_request:
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.x'
      - run: pip install mkdocs mkdocs-material
      - run: mkdocs gh-deploy --force
```

## AI Agent Guidelines

### When Modifying Content
- Maintain consistency with existing styling patterns (use same color schemes, borders, emoji conventions)
- Preserve the friendly, instructional tone used throughout
- Ensure technical accuracy for Garmin device instructions
- Keep sentences clear and accessible to non-technical users
- Test that markdown renders correctly in MkDocs

### When Adding New Sections
- Add corresponding entries to the `nav:` section in `mkdocs.yml`
- Use descriptive titles that match the markdown file heading
- Maintain alphabetical or logical ordering within categories
- For new model guides, place in `Articles/` subdirectory

### When Updating Navigation
- The `nav:` structure in `mkdocs.yml` determines sidebar and menu appearance
- Nested items under a parent (like "Articles:") create collapsible sections
- Keep paths relative to the `docs/` directory

## Repository Information

- **Documentation Source:** `docs/` directory in repository root
- **Configuration:** `mkdocs.yml`
- **Publishing:** GitHub Pages via `gh-pages` branch
- **Build Output:** `site/` directory (generated, not committed)

## Useful Links

- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Guide](https://www.markdownguide.org/)
