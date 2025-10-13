# QGIS Website Theme

A shared theme for QGIS-related websites containing **SCSS/SASS sources, compiled CSS, images and fonts**.  
This repository is intended to be used as a **Git submodule** (or linked in development via a symlink) so multiple projects can share consistent branding and styling.

---

## Table of contents

- [Repository structure](#repository-structure)  
- [Quick start](#quick-start)  
- [Development workflows](#development-workflows)  

---

## Repository structure

```
QGIS-Website-Theme/
├── scss/           # Primary SCSS entrypoints + partials (source)
├── webfonts/          # Web fonts used by the theme
├── images/         # Logos, icons, screenshots, etc.
└── README.md
```

> **Note:** `css/` may be committed to the repo (for simple inclusion) or generated during the project's build step. Include whichever workflow suits your CI/tooling.

---

## Quick start

### Add as a git submodule
From your project repository:

```bash
git submodule add https://github.com/qgis/QGIS-Website-Theme.git theme
git submodule update --init --recursive
```

This places the theme in `theme/` inside your project.

---

## Development workflows

### Edit inside submodule (fast, simple)
When the theme is a submodule, it is a normal git repo at `project/theme`. Edit files directly there:

```bash
cd project/theme
# edit scss/_variables.scss or scss/_buttons.scss
# then compile if needed, or reload your dev server (files are local)
```

When you're ready to share changes:

```bash
# inside project/theme
git add .
git commit -m "Improve button styles"
git push origin main

# in the parent project (to record the new submodule commit)
cd ..
git add theme
git commit -m "Update theme submodule pointer"
git push
```

You **do not** have to push just to test locally — edits inside `project/theme` are immediately visible to your project.
