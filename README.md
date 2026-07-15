# Green Gallery â€” Digital Exhibition Portfolio

A one-page portfolio for a Vietnamese IT student, designed around a "gallery walk" concept: the site is presented as a modern exhibition, with each section framed as a "room" (Giá»›i thiá»‡u, Dá»± Ã¡n, Ká»¹ nÄƒng, Tá»•ng káº¿t) and each project displayed like a curated artwork. The visual language uses a deep green / avocado green / sage palette with generous whitespace, large editorial typography (Be Vietnam Pro / Inter), soft shadows, glassmorphism accents, and scroll-triggered animations â€” inspired by Apple, Notion, Behance and modern museum exhibition sites.

## Tech stack

- TanStack Start (React 19 + TanStack Router) on Vite 7
- Tailwind CSS 4 with a custom green design-token theme
- Framer Motion for scroll reveals, page transitions and the loading splash
- Lucide React icons
- Deployed on Netlify

## Structure

- `src/data/site.ts` â€” all editable content (profile, bio, interests, projects, skills, timeline, contact links). Edit this file to update the site without touching component code.
- `src/components/gallery/` â€” one component per exhibition room/section.
- `src/routes/index.tsx` â€” composes the rooms into the single page.
- `src/styles.css` â€” fonts, green color tokens, global animation keyframes.

See `AGENTS.md` for a fuller architecture breakdown.

## Running locally

```bash
npm install
npm run dev
```

Then open the printed local URL. To build for production:

```bash
npm run build
```
