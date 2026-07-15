# AGENTS.md

Overview of the project structure for developers and AI agents working on this codebase.

## Project Overview

Green Gallery — a single-page portfolio for a CNTT (IT) student, designed as a modern "exhibition" (gallery walk) of the student's introduction, projects, skills, timeline and contact info. Built with TanStack Start and deployed on Netlify.

### Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | TanStack Start |
| Frontend | React 19, TanStack Router v1 |
| Build | Vite 7 |
| Styling | Tailwind CSS 4 (custom green theme tokens in `src/styles.css`) |
| Animation | Framer Motion |
| Icons | Lucide React |
| Language | TypeScript 5 (strict mode) |
| Deployment | Netlify |

## Directory Structure

```
├── public
│   ├── favicon.ico
│   └── headshot-on-white.jpg      # Portrait used in the Hero section
├── src
│   ├── components
│   │   ├── ui/                    # Small Radix-based primitives (Card, Badge)
│   │   └── gallery/                # All the "exhibition room" sections
│   │       ├── Reveal.tsx          # Scroll-in-view animation wrapper (Framer Motion)
│   │       ├── RoomHeader.tsx      # Shared "Room 0X — Title" heading block
│   │       ├── GalleryNav.tsx      # Sticky nav with blur-on-scroll
│   │       ├── GalleryLoader.tsx   # Splash loading animation
│   │       ├── Hero.tsx            # Two-column hero with framed portrait
│   │       ├── IntroRoom.tsx       # Room 01 — Bento grid: about/interests/direction/motto
│   │       ├── ProjectsRoom.tsx    # Room 02 — Project list + curator-note detail panel
│   │       ├── SkillsRoom.tsx      # Room 03 — Skill cards with progress bars
│   │       ├── TimelineRoom.tsx    # Learning/certificate/activity/experience timeline
│   │       ├── SummaryRoom.tsx     # Room 04 — Closing summary + quote
│   │       ├── ContactRoom.tsx     # Contact card + socials
│   │       └── GalleryFooter.tsx
│   ├── data
│   │   └── site.ts                 # ALL editable content lives here (profile, projects, skills, timeline, contact...)
│   ├── lib/utils.ts                 # cn() class merge helper
│   ├── routes
│   │   ├── __root.tsx               # Root HTML shell
│   │   └── index.tsx                # Composes every gallery room into the single page
│   ├── router.tsx
│   └── styles.css                   # Tailwind import, Be Vietnam Pro/Inter fonts, green theme tokens
├── netlify.toml
├── package.json
├── tsconfig.json
└── vite.config.ts
```

## Key Concepts

### Editing content

Nearly everything visible on the page (name, bio, tags, projects, skills, timeline entries, contact links) is defined in `src/data/site.ts`. Update that file to change content — no component code needs touching for typical edits (text, adding/removing a project, etc.).

### Design system

- Color tokens (`--gallery-deep #1B5E20`, `--gallery-avocado #A5D6A7`, `--gallery-sage #81C784`, background `#F8FBF7`) are defined in `src/styles.css` under `:root` and exposed as Tailwind colors (`gallery-deep`, `gallery-avocado`, `gallery-sage`, `gallery-bg`, `gallery-text`) via `@theme inline`. Most components currently use the raw hex values directly in class names for clarity — keep new sections consistent with the existing palette.
- Fonts: Be Vietnam Pro (primary) with Inter fallback, loaded via Google Fonts `@import` in `styles.css`.
- Scroll-reveal animations use the shared `Reveal` component (Framer Motion `whileInView`).

### File-Based Routing (TanStack Router)

- `__root.tsx` — root layout wrapping all pages
- `index.tsx` — the entire one-page site (`/`)

## Development Commands

```bash
npm run dev      # Start dev server
npm run build    # Production build
```

## Conventions

- Components: PascalCase, one exported component per file
- Content/data: kept out of components, centralized in `src/data/site.ts`
- Styling: Tailwind utility classes, `cn()` helper for conditional merges
- TypeScript strict mode; `@/` path alias maps to `src/`
