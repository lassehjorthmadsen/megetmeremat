# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Meget mere mat** is a Danish Quarto book project about mathematics for curious elementary school students. The book is authored by Selma and Lasse (father-daughter collaboration) and published at [https://megetmeremat.dk](https://megetmeremat.dk).

## Development Commands

### Building and Rendering
- `quarto render` - Build the entire book to `docs/` directory
- `quarto preview` - Start local development server with live reload

### Git Configuration
This is a personal side project. Always use the personal email for commits:
```bash
git config user.name "Lasse Hjorth Madsen"
git config user.email "lassehjorthmadsen@gmail.com"
```

## Architecture

### Book Structure
The project is configured as a Quarto book (`_quarto.yml`) with Danish language settings:
- **Output**: HTML format with Cosmo theme, outputs to `docs/` for GitHub Pages
- **Language**: Danish (`lang: "da"`)
- **Authors**: "Selma og Lasse"
- **Execution**: R code chunks with `freeze: auto` for caching

### Chapter Organization
Chapters are individual `.qmd` files with minimal YAML frontmatter (title only):
1. `index.qmd` - Introduction/landing page
2. `parabler.qmd` - Parabolas (uses tidyverse + theme_minimal)
3. `enheder.qmd` - Units (text-only, no R setup)
4. `potenser-rodder.qmd` - Powers & Roots (text-only, no R setup)
5. `logaritmer.qmd` - Logarithms (uses tidyverse + latex2exp)
6. `differentialregning.qmd` - Differential Calculus (uses tidyverse)
7. `kombinatorik.qmd` - Combinatorics (uses tidyverse + igraph)

### R Package Dependencies
Each chapter loads only the packages it needs:
- **tidyverse**: Data manipulation and plotting (most chapters)
- **latex2exp**: Mathematical expressions in plots
- **igraph**: Graph/network visualizations for combinatorics

### Publishing Setup
- **GitHub Pages**: Serves from `docs/` directory
- **Custom Domain**: `megetmeremat.dk` (configured via `docs/CNAME`)
- **Jekyll Disabled**: `docs/.nojekyll` prevents Jekyll processing
- **Cache Management**: `_freeze/` directory excluded from git via `.gitignore`

## Key Conventions

### Chapter Structure
- Chapters use YAML frontmatter with `title` field only
- R setup blocks named `{r setup}` consistently
- Section IDs follow pattern `{#sec-chaptername}` for cross-references
- Danish language throughout content

### Git Workflow
- Main branch: `main`
- Auto-deployment via GitHub Pages on push to main
- `_freeze/` cache directory ignored (speeds up local rendering)
- Always use personal email for this side project
- Be mindful to keep 'docs/CNAME' and 'docs/.nojekyll' files, since these are needed for GitHub to serve the site at megetmeremat.dk