# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

A decorative animated flower gift website. Users land on a teaser page (`index.html`) with a typing animation, then click "Open" to reveal an animated flower bouquet with a message (`flower.html`).

## Development Commands

**Compile SCSS to CSS:**
```powershell
sass scss/style.scss css/style.css --source-map
```

**Watch SCSS for changes:**
```powershell
sass --watch scss/style.scss:css/style.css
```

**Local preview:** Open `index.html` directly in browser or use a local server:
```powershell
npx serve .
```

## Architecture

### Page Flow
`index.html` → (click "Open") → `flower.html`

### Styling Pattern
- **SCSS source**: `scss/style.scss` compiles to `css/style.css`
- **BEM naming**: `.flower__leaf--1`, `.flower__line__leaf--2`
- **Viewport units**: Uses `vmin` throughout for responsive scaling
- **CSS variables**: Theme colors defined in `:root` (e.g., `--dark-color`)

### Animation System
The flower animation in `style.scss` uses:
- Sequenced `animation-delay` values via SCSS loops for staggered bloom effects
- `--d` CSS variable for delay timing on `.grow-ans` elements
- `.not-loaded` class on body pauses all animations until page loads
- `@keyframes` for bloom, sway, and particle light effects

### JavaScript
- `js/index.js`: Typewriter effect for landing page title
- `js/main.js`: Removes `.not-loaded` class after 1s delay to start animations, then types the message letter-by-letter

## Deployment

Automated via GitHub Actions (`.github/workflows/static.yml`) - pushes to `main` deploy to GitHub Pages.

## Customization Points

- **Message text**: Change `'I LOVE U'` in `js/main.js` and `'I Have Something'` in `js/index.js`
- **Color palette**: Modify CSS variables in `:root` and gradient values in SCSS
- **Animation timing**: Adjust `animation-delay` and `--d` values in SCSS
