# ASTEMON - Technical Documentation

**ASTEMON** is a user-friendly waste sorting guide for Lisbon, designed for tourists, expats, and exchange students. This project aims to make waste management accessible, visual, and easy to understand through an interactive learning experience.

## Table of Contents

- [Project Overview](#project-overview)
- [Naming Conventions](#naming-conventions)
- [Branches](#branches)
- [Workflow](#workflow)
- [Project Structure](#project-structure)
- [CSS](#css)
  - [Fonts](#fonts)
  - [Colors](#colors)
  - [Styles](#styles)
  - [Media Queries](#media-queries)
  - [Units](#units)
- [Components](#components)
- [Pages](#pages)
- [Components & Layout](#components--layout)
  - [Props](#props)
  - [Slots](#slots)
- [Scripts](#scripts)
- [AOS (Animate On Scroll)](#aos-animate-on-scroll)
- [Database Usage](#database-usage)
- [Accessibility](#accessibility)
- [Commands](#commands)
- [Conclusion](#conclusion)

---

## Project Overview

ASTEMON is built with **Astro**, a modern static site generator framework. The project provides:

- **Sorting Guide**: Detailed information on how to sort waste in Lisbon by bin color
- **Interactive Experience**: A gamified experience where users become trash and make sorting decisions
- **Life Cycle of Waste**: Educational content about waste degradation

---

## Naming Conventions

- **Component files**: PascalCase (e.g., `Welcome.astro`, `DecomSection.astro`)
- **Asset files**: lowercase with descriptive names (e.g., `hero_graphic.svg`, `logo_watermark_tagline.svg`)
- **CSS classes**: lowercase with hyphens (e.g., `.hero_div`, `.intro-section`)

---

## Branches

Branch naming convention: `name-feature-description`

---

## Workflow

1. **Communication First**: Discuss feature distribution before coding
2. **Ownership**: Don't modify another team member's file without permission
3. **Commit Messages**:
   - Major changes: Descriptive message (e.g., "Add hero section with video and animations")
   - Minor changes: "fixes", "updates", etc.
4. **Merging**: Notify the team when merging large features via Teams/Messenger

---

## Project Structure

```
/
├── public/
│   ├── img/
│   │   ├── hero_graphic.svg
│   │   ├── logo_giant.svg
│   │   ├── globe.svg
│   │   └── [other image assets]
│   ├── astemon.mov
│   ├── astemon-kopi.mp4
│   └── favicon.svg
│
├── src/
│   ├── components/
│   │   ├── AboutSDG.astro
│   │   ├── Banner.astro
│   │   ├── BoxButton.astro
│   │   ├── DecomSection.astro
│   │   │   └── Handles accordion-style decomposition timeline
│   │   ├── DeItem.astro
│   │   │   └── Individual accordion item for decomposition times
│   │   ├── DidYouKnow.astro
│   │   │   └── Educational teaser section about waste
│   │   ├── FeatureGrid.astro
│   │   │   └── Grid layout for main feature cards
│   │   ├── Footer.astro
│   │   │   └── Footer with links and contact info
│   │   ├── Header.astro
│   │   │   └── Main navigation header (desktop + mobile burger menu)
│   │   ├── HEADER2.astro
│   │   │   └── Secondary header variant with different styling
│   │   ├── IESection.astro
│   │   │   └── Interactive Experience section with CTA
│   │   ├── SortIntro.astro
│   │   │   └── Introduction section for sorting guide
│   │   ├── TextButton.astro
│   │   │   └── Text-based button component
│   │   └── Welcome.astro
│   │       └── Welcome/hero introduction section
│   │
│   ├── layouts/
│   │   └── Layout.astro
│   │       └── Main layout wrapper with head, header, footer
│   │
│   ├── pages/
│   │   ├── index.astro
│   │   │   └── Homepage with hero, features, and CTAs
│   │   ├── guide.astro
│   │   │   └── Sorting guide page with detailed categories
│   │   ├── cycle.astro
│   │   │   └── Life cycle of waste educational page
│   │   └── about.astro
│   │       └── About ASTEMON and SDG 11 page
│   │
│   └── styles/
│       └── generel.css
│           └── Global styles, resets, media queries, CSS variables
│
├── .gitignore
├── astro.config.mjs
├── package.json
├── package-lock.json
├── tsconfig.json
└── README.md
```

### Component Descriptions

#### Layout Components

- **Layout.astro**: Wrapper layout with meta tags, fonts, AOS initialization, header, footer

#### Header & Navigation

- **Header.astro**: Header with burger menu for mobile, scroll prevention

#### Hero & Featured Sections

- **Welcome.astro**: Main welcome section with tagline and CTA
- **Banner.astro**: Visual banner section with styling
- **DidYouKnow.astro**: Educational teaser section with fade-right AOS animation

#### Sorting Guide Components

- **SortIntro.astro**: Introduction to sorting with image and CTA button
- **FeatureGrid.astro**: Grid layout showcasing main features/waste categories

#### Interactive Experience

- **IESection.astro**: "Learning by Doing" section with interactive experience CTA and animated graphic

#### Decomposition Timeline

- **DecomSection.astro**: Main accordion container for decomposition times
- **DeItem.astro**: Individual accordion item with title and content (uses `set:html` for formatting)

#### Educational Content

- **AboutSDG.astro**: Information about Sustainable Development Goal 11

#### Buttons

- **TextButton.astro**: Simple text-based button with hover effects
- **BoxButton.astro**: Box-styled button with border and hover animation

#### Footer

- **Footer.astro**: Footer with copyright, links, and social media

---

## CSS

### Fonts

Fonts are loaded via Google Fonts in `Layout.astro`:

- **Headings**: Lexend Giga, Lexend Mega, Archivo Narrow
- **Body text**: Roboto

```astro
<link
  href="https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100..900;1,100..900&display=swap"
  rel="stylesheet"
/>
<link
  href="https://fonts.googleapis.com/css2?family=Lexend+Giga:wght@100..900&display=swap"
  rel="stylesheet"
/>
<link
  href="https://fonts.googleapis.com/css2?family=Archivo+Narrow:ital,wght@0,400..700;1,400..700&display=swap"
  rel="stylesheet"
/>
```

### Colors

CSS custom properties defined in root:

```css
html {
  --green: #bef5c8;
  --light_green: #e8f9ee;
  --ashbrown: #6b6b6b;
  --white: #ffffff;
  --black: #000000;
}
```

### Styles

- **Reset**: Removes default margins, padding, and styles
- **Whitespace**: `.white_space` class for section spacing
- **Responsive images**: `width: 100%`, `height: auto`, `object-fit: cover`

### Media Queries

Responsive breakpoints:

- Mobile: `max-width: 600px`
- Tablet: `max-width: 1024px`
- Desktop: `min-width: 1025px`

### Units

- **Pixels (px)**: Precise control over whitespace and spacing
- **REM (rem)**: Scalable typography based on root font size

---

## Components

### Core Components

| Component | Purpose                                | Location                      |
| --------- | -------------------------------------- | ----------------------------- |
| `Layout`  | Main wrapper with head, header, footer | `src/layouts/Layout.astro`    |
| `Header`  | Desktop navigation with burger menu    | `src/components/Header.astro` |
| `Footer`  | Footer with links and info             | `src/components/Footer.astro` |

### Hero & Featured Sections

| Component     | Purpose               | Location                           |
| ------------- | --------------------- | ---------------------------------- |
| `Welcome`     | Main welcome section  | `src/components/Welcome.astro`     |
| `Banner`      | Visual banner section | `src/components/Banner.astro`      |
| `DidYouKnow`  | Educational teaser    | `src/components/DidYouKnow.astro`  |
| `FeatureGrid` | Grid of main features | `src/components/FeatureGrid.astro` |

### Guide & Experience Sections

| Component   | Purpose                        | Location                         |
| ----------- | ------------------------------ | -------------------------------- |
| `SortIntro` | Sorting guide introduction     | `src/components/SortIntro.astro` |
| `IESection` | Interactive experience section | `src/components/IESection.astro` |

### Decomposition Timeline

| Component      | Purpose                   | Location                            |
| -------------- | ------------------------- | ----------------------------------- |
| `DecomSection` | Main accordion container  | `src/components/DecomSection.astro` |
| `DeItem`       | Individual accordion item | `src/components/DeItem.astro`       |

### Educational & Info

| Component  | Purpose                    | Location                        |
| ---------- | -------------------------- | ------------------------------- |
| `AboutSDG` | SDG 11 sustainability info | `src/components/AboutSDG.astro` |

### Buttons

| Component    | Purpose            | Location                          |
| ------------ | ------------------ | --------------------------------- |
| `TextButton` | Simple text button | `src/components/TextButton.astro` |
| `BoxButton`  | Box-styled button  | `src/components/BoxButton.astro`  |

---

## Pages

### `index.astro` (Home)

- Hero section with video background and animated SVG
- Brand green tint overlay
- Pulse animation on graphic
- Chevron-style scroll CTA
- Welcome section
- Feature grid
- Banner
- Interactive experience promo

**Location**: `src/pages/index.astro`

### `guide.astro` (Sorting Guide)

- Sorting introduction with globe graphic
- Feature grid with waste categories
- Detailed sorting instructions by bin color

**Location**: `src/pages/guide.astro`

### `cycle.astro` (Life Cycle)

- "Did You Know?" educational section
- Interactive decomposition timeline with accordion
- Decomposition times for common items:
  - Plastic Bag (10-20 years)
  - Chewing Gum (5-25 years)
  - Fishing Line (600 years)
  - Plastic Bottle (400-1000 years)
  - Paper Bag (1 month)
  - Glass (1 million years)
  - [and more]

**Location**: `src/pages/cycle.astro`

### `about.astro` (About)

- Project motivation and background
- Research findings
- SDG 11 sustainability commitment
- Team information

**Location**: `src/pages/about.astro`

---

## Components & Layout

### Props

Pass data to components:

```astro
---
interface Props {
  title: string;
  content: string;
  buttonurl?: string;
  buttontext?: string;
}

const { title, content, buttonurl, buttontext } = Astro.props;
---
```

### Slots

Dynamic content insertion:

```astro
<div class="container">
  <slot />
</div>
```

---

## Scripts

### Video Playback Control (`index.astro`)

Slows down hero video to 70% speed:

```js
document.addEventListener("DOMContentLoaded", () => {
  const video = document.querySelector(".hero_video");
  if (video) {
    video.playbackRate = 0.7;
  }
});
```

### Mobile Menu Toggle (`Header.astro`)

Handles burger menu animation and scroll prevention:

```js
const burger = document.querySelector(".burger");
const nav = document.querySelector("nav");
const menu = document.querySelector(".menu");

function disableScroll() {
  scrollPosition = window.pageYOffset;
  document.body.style.position = "fixed";
  document.body.style.top = `-${scrollPosition}px`;
}

function enableScroll() {
  document.body.style.position = "";
  window.scrollTo(0, scrollPosition);
}

if (burger && nav && menu) {
  burger.addEventListener("click", () => {
    burger.classList.toggle("active");
    const isActive = nav.classList.toggle("active");
    if (isActive) disableScroll();
    else enableScroll();
  });
}
```

### Accordion Toggle (`DecomSection.astro`)

Opens/closes accordion items with smooth height animation:

```js
const closeAccordion = (acc) => {
  const content = acc.querySelector(".decomp-content");
  acc.classList.remove("is-open");
  if (content) content.style.maxHeight = "0px";
};

const openAccordion = (acc) => {
  const content = acc.querySelector(".decomp-content");
  acc.classList.add("is-open");
  if (content) content.style.maxHeight = content.scrollHeight + "px";
};
```

### Smooth Scroll (`index.astro`)

Smooth scrolling to anchor links:

```css
html {
  scroll-behavior: smooth;
}
```

---

## AOS (Animate On Scroll)

AOS library integrated via CDN for scroll-triggered animations.

**Installation** (already done in `Layout.astro`):

```html
<link rel="stylesheet" href="https://unpkg.com/aos@2.3.1/dist/aos.css" />
<script defer src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
<script>
  document.addEventListener("DOMContentLoaded", () => {
    if (window.AOS) {
      window.AOS.init({ duration: 600, once: true });
    }
  });
</script>
```

**Usage**:

```astro
<div data-aos="fade-up">Content animates on scroll</div>
<div data-aos="fade-right">Content slides in from left</div>
<div data-aos="zoom-in">Content zooms in</div>
```

Available animations:

- `fade-up`, `fade-down`, `fade-left`, `fade-right`
- `zoom-in`, `zoom-out`, `flip-left`, `flip-right`
- `bounce`, `pulse`, `slide-up`, `slide-down`

---

## Database Usage

Currently, ASTEMON does not use an external database. All content is statically generated using Astro components.

**Future implementation** (if needed):

- Supabase could be integrated for dynamic content (waste categories, decomposition times)
- API endpoints would fetch data at build time

---

## Accessibility

- **Semantic HTML**: Proper use of `<section>`, `<article>`, `<nav>`, etc.
- **ARIA labels**: `aria-hidden` for decorative elements, `aria-label` for buttons
- **Screen reader support**: Text alternatives for images, descriptive button labels
- **Keyboard navigation**: All interactive elements are keyboard accessible
- **Color contrast**: Sufficient contrast ratios for text and buttons
- **Focus indicators**: Visible focus states for keyboard users

---

## Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

---

## Dependencies

- **Astro**: Static site generator
- **AOS**: Scroll animation library

---

## Conclusion

ASTEMON is a modern, accessible, and visually engaging platform designed to make waste sorting in Lisbon easy and intuitive. By combining responsive design, interactive components, and smooth animations, the project delivers an educational experience that empowers users to sort waste correctly and contribute to a more sustainable city.

The component-based architecture in Astro ensures scalability and maintainability, while accessibility-first practices make the content available to all users, regardless of ability.

---

**For more information, visit the Astro documentation**: [docs.astro.build](https://docs.astro.build)
