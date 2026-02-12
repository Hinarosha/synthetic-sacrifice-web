## Synthetic Sacrifice – Web Overview

This project is a narrative and design overview for a cyberpunk 2D/3D RPG, presented as a single-page React application.  
This web app lets you browse the game’s inspirations, story arcs, characters, endings and design notes in a structured, scrollable layout with a navigation sidebar and theme switcher.

This project is soon gonna change to probably a Next.js app or anything else that would look good enough to present the game.

The actual game design document also lives in `game.txt`; the React app in `src/App.tsx` renders a curated, navigable version of that content.

---

## Tech Stack

- **Framework**: React + TypeScript
- **Bundler/Dev server**: Vite
- **UI utilities**: `react-icons`, `framer-motion` (planned/available), custom CSS

---

## Getting Started

### Prerequisites

- **Node.js** and **npm** installed (any current LTS should work fine).

### Install dependencies

```bash
npm install
```

### Run the dev server

```bash
npm run dev
```

Then open the URL printed in the terminal (by default `http://localhost:5173`) in your browser.

### Lint the code

```bash
npm run lint
```

### Create a production build

```bash
npm run build
```

### Preview the production build

```bash
npm run preview
```

---

## Project Structure (high level)

- **`src/main.tsx`**: React entry point; mounts `App` into the `#root` element.
- **`src/App.tsx`**: Main UI. Defines the section hierarchy (introduction, story beats, endings, characters, design, etc.), renders the sidebar navigation, tracks the active section with an `IntersectionObserver`, and wires the dark/light theme through `ThemeSwitch`.
- **`game.txt`**: Original game design document (inspiration, story outline, endings, characters, bosses, design and development notes). `App.tsx` contains a structured version of this content tailored for the web view.
- **`ThemeSwitch` and CSS files**: Handle theme toggling and overall layout/styling of the cyberpunk-inspired page.

---

## How the Page Works

- **Sidebar navigation**:  
  - **Parent sections** (e.g. Story, Characters) appear as main buttons.  
  - **Child sections** (e.g. The Awakening, Optional Bosses) appear as indented sub-items.
- **Scroll tracking**:  
  - Each section is assigned a `ref` and observed via `IntersectionObserver`.  
  - The currently visible section updates `activeSection` so the matching nav item is highlighted.
- **Theme switching**:  
  - The `ThemeSwitch` component calls `onThemeChange('light' | 'dark')`.  
  - `App` updates `darkMode` and applies either `dark-theme` or `light-theme` on `document.body`.

If you extend the app (for example, to add new sections or animations), keep using the existing `Section` type and `mainSections` structure so the sidebar and scroll tracking continue to work consistently.

---

## About the Game Concept

Synthetic Sacrifice is a 2D-3D hybrid cyberpunk RPG concept where:

- **The player** wakes up dismembered and amnesiac, scavenging cybernetics to survive.
- **Choices** around factions (rebels vs corpos), key characters (like Grim Fang and Z) and cybernetic overuse lead to **seven different endings**.
- **Gameplay vision** mixes click-based exploration, turn-based combat and an upgrade tree for cybernetics.
- **World design** spans a neon mega-city, lawless undercity and hostile desert full of cyberpsychos and optional bosses.

For the full narrative and design details, see both the web app sections and the `game.txt` document.
