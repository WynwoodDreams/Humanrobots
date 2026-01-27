# CLAUDE.md - RobotHub Codebase Guide

## Project Overview

**RobotHub** is an interactive web showcase dedicated to displaying and cataloging humanoid robots from various companies. It presents the state of embodied AI with news, specs, and interactive visualizations of 9 different humanoid robot models.

This is a **static website** with no build system - all files can be opened directly in a browser.

## Quick Start

```bash
# No installation required - simply open any HTML file in a browser:
open index.html        # Full vanilla HTML/CSS/JS implementation
open index_react.html  # React-based implementation
open robot_hero.html   # Minimalist hero visualization
```

## Directory Structure

```
/home/user/Humanrobots/
├── CLAUDE.md              # This file - AI assistant guide
├── index.html             # Main vanilla HTML/CSS/JS implementation (~1200 lines)
├── index_react.html       # React-based implementation (~340 lines)
├── robot_hero.html        # Advanced hero/spotlight visualization (~200 lines)
├── robot_lineup.png       # Main hero image with all robots
├── .gitignore             # Git ignore file
├── assets/                # Robot image assets (PNG files)
│   ├── robot_apollo.png
│   ├── robot_atlas.png
│   ├── robot_digit.png
│   ├── robot_eve.png
│   ├── robot_figure.png
│   ├── robot_gr1.png
│   ├── robot_neo.png
│   ├── robot_optimus.png
│   └── robot_phoenix.png
└── news_*.png             # News section hero images
    ├── news_atlas.png
    ├── news_digit.png
    ├── news_figure.png
    ├── news_neo.png
    └── news_optimus.png
```

## Technology Stack

### Core Technologies
- **HTML5** - Semantic markup
- **CSS3** - Custom properties, animations, Grid/Flexbox layouts
- **Vanilla JavaScript** - DOM manipulation, event handling

### React Implementation (index_react.html)
- **React 18** - Component-based UI (loaded via CDN)
- **Tailwind CSS 3** - Utility-first CSS framework
- **Framer Motion** - Animation library
- **Lucide React** - Icon library
- **Babel Standalone** - JSX transpilation in browser

### External Resources (CDN)
All dependencies are loaded from CDN - no npm/node_modules required:
- React/ReactDOM from unpkg
- Tailwind CSS from CDN
- Google Fonts: Inter, Oswald, JetBrains Mono

## Code Architecture

### Three Implementation Approaches

1. **index.html** - Full-featured vanilla implementation
   - Interactive hover zones on robot lineup image
   - Sticky stats panel with detailed robot specs
   - News section with featured articles
   - Video gallery with embedded YouTube videos
   - Complete CSS styling inline

2. **index_react.html** - React modernization
   - Functional components with hooks
   - Framer Motion for smooth animations
   - Same functionality, more compact code
   - Components: `RobotCard`, `StatsPanel`, `NewsCard`, `App`

3. **robot_hero.html** - Minimalist hero visualization
   - Focus on 5 core robot models
   - Full-screen immersive experience
   - Simplified animation system

### Robot Data Structure

All implementations share a common data structure for robots:

```javascript
const robotsData = {
  "figure": {
    id: "figure",
    name: "Figure 02",
    company: "Figure AI",
    valuation: "$2.6B",
    status: "Production",     // Production | Pilot | Prototype
    height: "170cm",
    weight: "70kg",
    payload: "20kg",
    dof: "40+ DoF",
    speed: 85,                // 0-100 percentage
    efficiency: 78,           // 0-100 percentage
    tags: ["Humanoid", "Factory", "Logistics"],
    newsLink: "...",
    video: "YouTube embed URL"
  },
  // ... more robots
};
```

## Design System

### Color Palette
```css
--bg-void: #0a0a0a;           /* Main background */
--text-main: #f5f5f5;         /* Primary text */
--acid: #D4FF00;              /* Accent color (production status) */
--accent-blue: #00BFFF;       /* Pilot status */
--accent-red: #FF4136;        /* Prototype status */
--border-dark: #333;          /* Border color */
```

### Typography
- **Headings**: Oswald (bold, uppercase)
- **Body**: Inter
- **Monospace/Technical**: JetBrains Mono

### Design Philosophy
- **Brutalist aesthetic**: Sharp corners, solid borders, minimal shadows
- **Dark theme**: Near-black background with high contrast
- **Color coding**: Status indicated by accent colors (green/blue/red)
- **Grid textures**: Subtle background patterns

## CSS Conventions

### Naming Patterns
- BEM-inspired: `.robot-card`, `.stats-panel-sticky`, `.hover-zone`
- State classes: `.active`, `.hovered`
- Utility classes: `.glitch-hover`, `.mono`, `.uppercase`

### Key CSS Classes
```css
.robot-card        /* Individual robot display card */
.stats-panel       /* Robot specifications panel */
.hover-zone        /* Interactive clickable areas */
.news-grid         /* News article layout */
.video-gallery     /* Video embed container */
```

## JavaScript Patterns

### Vanilla JS (index.html)
- Event delegation with `mouseenter`/`mouseleave`
- Data-driven rendering with template literals
- Class toggling for state management
- No external frameworks

### React (index_react.html)
```jsx
// Functional components with hooks
const [activeId, setActiveId] = useState("figure");

// Framer Motion for animations
<motion.div
  initial={{ opacity: 0 }}
  animate={{ opacity: 1 }}
  exit={{ opacity: 0 }}
>
```

## Development Workflow

### No Build System Required
This is a static HTML project:
- No package.json or npm dependencies
- No webpack/vite/build configuration
- No compilation step needed
- Simply edit HTML/CSS/JS and refresh browser

### Testing
- No automated testing framework
- Quality verification is manual/visual
- Test in multiple browsers for compatibility

### Deployment
Ready for immediate deployment to any static hosting:
- GitHub Pages
- Netlify
- Vercel
- Any web server serving static files

## Working with This Codebase

### Adding a New Robot
1. Add robot image to `/assets/robot_[name].png`
2. Add entry to `robotsData` object in the HTML file(s)
3. For `index.html`: Add corresponding hover zone coordinates
4. Add any news images as `news_[name].png`

### Modifying Styles
- Global CSS variables are in `:root` selector
- Component styles follow the class conventions above
- Tailwind classes available in React version

### Common Tasks

**Change accent color:**
```css
:root {
  --acid: #YOUR_COLOR;
}
```

**Add new robot to data:**
```javascript
robotsData["newrobot"] = {
  id: "newrobot",
  name: "New Robot",
  company: "Company Name",
  // ... other properties
};
```

**Modify hover zone positions (index.html):**
```css
.hover-zone[data-robot="newrobot"] {
  left: X%;
  width: Y%;
}
```

## File Reference

| File | Lines | Purpose |
|------|-------|---------|
| `index.html` | ~1,200 | Full vanilla implementation with all features |
| `index_react.html` | ~340 | React/Tailwind modernized version |
| `robot_hero.html` | ~200 | Minimalist hero visualization |

## Featured Robots

1. **Figure 02** (Figure AI) - Production status
2. **Phoenix** (Sanctuary AI) - Prototype status
3. **Atlas** (Boston Dynamics) - Pilot status
4. **GR-1** (Fourier Intelligence) - Production status
5. **Digit** (Agility Robotics) - Pilot status
6. **EVE** (1X Technologies) - Production status
7. **NEO** (1X Technologies) - Prototype status
8. **Optimus Gen 3** (Tesla) - Pilot status
9. **Apollo** (Apptronik) - Pilot status

## Notes for AI Assistants

- This is a **static website** - no build commands needed
- All code is inline within HTML files
- When editing, maintain the brutalist design aesthetic
- Keep the existing data structure format when adding robots
- Test changes by opening HTML files directly in browser
- The React version mirrors vanilla functionality - keep them in sync if modifying features
