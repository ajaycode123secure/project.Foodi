# Copilot Instructions for Cakery Project

## Project Overview
**Cakery** is a vanilla HTML/CSS/JavaScript frontend for a bakery website. Currently in early development with a basic navbar; progressive expansion planned for product showcases, ordering, and responsive design.

## Architecture & Current State

### Three-File Core Structure
- **[indix.html](../indix.html)** (⚠️ filename typo: should be `index.html`)
  - Minimal structure: `<header>` with navbar only; body mostly empty
  - Logo: "Cake" + colored "ry." span using CSS variables
  - Navigation: 6 links (Home, About, Menu, Restaurant, Order, Contact)
  - Right icons: User and cart shopping icons (Font Awesome)
  - **BUG**: Script tag malformed: `<scrip scr="javascrip.js">` (should be `<script src="javascrip.js">`)

- **[style.css](../style.css)** - Responsive styling with multiple font families imported
  - **CSS Variables** (`:root`): `--orange` (#FF8C00), `--forest-mint`, `--white`, `--black`, `--gray`, `--light-gray`, `--dusty-pink`
  - **CRITICAL BUG**: CSS classes use undefined variables `--orange-clr`, `--black-clr` (defined as `--orange`, `--black` only)
  - **SYNTAX BUGS**: 
    - `.icon-link` missing semicolon after `border-radius: 50%`
    - `display: inline block` should be `inline-block`
  - Layout: Flexbox navbar with `justify-content: space-around`
  - `.container`: 80% width centered wrapper
  - Fonts: Google Fonts (primary: Roboto; also: DM Serif, Poppins, Lato, Fira Sans, etc.)

- **[javascrip.js](../javascrip.js)** (⚠️ filename typo: should be `javascript.js`)
  - Currently empty; ready for interactivity

## Known Issues & Conventions

### Critical Bugs (Must Fix First)
1. **HTML script tag**: `<scrip scr="">` → change to `<script src="javascrip.js">`
2. **CSS variable mismatch**: Code references `--orange-clr`, `--black-clr` but only `--orange`, `--black` exist in `:root`
3. **CSS syntax**: Missing semicolon on `border-radius: 50%`; `inline block` → `inline-block`
4. **Class naming inconsistency**: `.Active` (inconsistent case—should be `.active`)

### CSS Patterns
- **Colors**: Define in `:root` CSS variables; orange (#FF8C00) is primary accent
- **Layout**: Flexbox for navbar; `.container` wrapper at 80% width
- **Hover effects**: `.navlinks:hover`, `.icon-link:hover` with `transform: translate(-10%)`
- **Icons**: Font Awesome v7.0.1 (SRI integrity hash, CSS only, no JS needed)

### HTML Conventions
- All nav links use `href="#"` (placeholders—implement routing/smooth scroll)
- Semantic structure: `<header>` wraps navbar; logo and nav sections in `.navbar` flex container
- Icons wrapped in `.nav-icon` div

## Development Roadmap

### Phase 1: Fix Critical Issues
1. Correct malformed script tag
2. Align CSS variable names across codebase
3. Fix syntax errors (semicolons, `inline-block`)
4. Verify all colors render correctly

### Phase 2: Expand Content
1. Add hero section below navbar
2. Build product/menu cards grid (reuse flexbox pattern from navbar)
3. Add footer
4. Implement responsive breakpoints (mobile < 768px)

### Phase 3: Interactivity
1. Add click handlers for nav links (smooth scroll or routing)
2. Cart icon interaction (increment/update count)
3. Mobile menu toggle if hamburger added

## File Organization
- `indix.html` → main HTML entry (fix filename when deploying)
- `style.css` → single stylesheet (no SCSS/preprocessor)
- `javascrip.js` → vanilla JS (no frameworks)
- `image/images/` → image assets folder
- No build system, no package.json, no node_modules (keep minimal)

## External Dependencies
- **Font Awesome 7.0.1**: CDN CSS with SRI hash (no JS required)
- **Google Fonts**: 7 font families; primary is Roboto

## AI Agent Notes
- Preserve filename typos (`indix.html`, `javascrip.js`) unless user explicitly requests rename
- Prioritize fixing CSS variable mismatch and script tag before adding features
- When adding HTML sections, follow navbar flexbox pattern for consistency
- Keep vanilla JS; avoid frameworks
