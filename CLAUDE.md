# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file static portfolio website for **Abdoul Majid Aboubacar Mahamadou**, a mechatronics engineer. The entire site lives in `index.html` — there is no build system, no package manager, and no framework.

To preview: open `index.html` directly in a browser (double-click or drag into browser).

## Architecture

Everything is in one file (`index.html`):
- **CSS** — in a `<style>` block in `<head>`. Uses CSS custom properties defined on `:root` for the color palette (`--bg`, `--surface`, `--accent`, `--accent-light`, `--border`, `--text`, `--muted`).
- **HTML** — sections in order: `#hero`, `#about`, `#skills`, `#experience`, `#projects`, `#gallery`, `#certificates`, `#contact`.
- **JS** — inline `<script>` at bottom. Contains three functions: `handleSubmit` (contact form → mailto), `openLightbox`/`closeLightbox` (gallery lightbox), `nextSlide` (project card image carousel).

## Asset Structure

```
index.html
project pictures/       # Project photos — referenced as "project pictures/filename"
Personnal_pictures/     # Profile photo + activity/event photos
certificates/
  attachments/          # Certificate images — referenced as "certificates/attachments/filename"
```

All image paths in HTML are relative, so the folder structure must stay intact when deploying.

## Content Conventions

- **Skills** — each skill is a `.skill-card` div with an emoji icon, a `.skill-name`, and a `.skill-sub` for the tool/detail.
- **Projects** — each `.project-card` contains a `.project-gallery` (supports multiple images via `nextSlide`) and a `.project-body`. Add new images to `project pictures/` and reference them in the gallery block.
- **Certificates** — each `.cert-card` has a `.cert-thumb` containing an `<img>`, a `.cert-title`, `.cert-issuer`, and `.cert-date`.
- **Gallery (activities)** — each `.gallery-item` calls `openLightbox('path', 'caption')` on click.

## Deployment

No build step needed. To deploy:
- **GitHub Pages**: push the repo and enable Pages from the root.
- **Netlify / Vercel**: drag-and-drop the project folder.
- Ensure all asset folders are included — the site breaks without them since all paths are relative.
