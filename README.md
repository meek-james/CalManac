# CalManac

A mobile-first coursework tracker for Fall 2026 — one place to see what's due, across every class, on your phone.

Styled to sit alongside the IDNTT training app: same warm-charcoal, Solar Gold (`#ffaa00`) identity, same "open it on your phone and just use it" philosophy. No login, no backend, no build step.

## What it does

- Tracks assignments across your four Fall 2026 classes: **IEOR 115** (Database Design), **ENGIN 7**, **SOC 111AC**, **IND ENG 174**
- Tabs to filter by class, or view everything under **All**
- Each assignment has a title, type (Homework / Reading / Quiz / Exam / Project / Other), due date, and optional notes
- Color-coded due badges: red for today/tomorrow/overdue, gold for due within a week, neutral further out, green once complete
- A stat line up top ("3 due this week", "1 overdue, 2 due this week") that always reflects everything across all classes, even while you're filtered to one tab
- Tap any assignment to edit or delete it; tap the circle to mark it done
- Everything is stored locally in the browser (`localStorage`) — nothing leaves your device, no account needed

## Using it

Just open `index.html` in a browser. That's it. On mobile, add it to your home screen (Share → Add to Home Screen on iOS) for something close to an app icon and full-screen feel.

## Deploying it (GitHub Pages, same pattern as idntt-training-app)

1. Create a new repo, e.g. `calmanac`
2. Push `index.html` to it
3. In the repo's Settings → Pages, set the source to the `main` branch, root folder
4. It'll be live at `https://<your-username>.github.io/calmanac/`

## Customizing

Everything class-related lives in one place near the top of the `<script>` block in `index.html`:

```js
const CLASSES = [
  { id: 'ieor115',   code: 'IEOR 115',    name: 'Database Design' },
  { id: 'engin7',    code: 'ENGIN 7',     name: 'Intro to Programming & Numerical Methods' },
  { id: 'soc111ac',  code: 'SOC 111AC',   name: 'Sociology of the Family' },
  { id: 'indeng174', code: 'IND ENG 174', name: 'Simulation for Enterprise-Scale Systems' },
];
```

Add, remove, or rename classes here for a new semester — the tabs and dropdowns rebuild from this list automatically. `id` just needs to stay unique; `code` is what shows on tabs and cards.

The color tokens (background, Solar Gold accent, status colors) are CSS variables at the top of the `<style>` block if you want to adjust the palette.

## A note on data

Assignments are saved to the browser's `localStorage`, scoped to whichever browser and device you're using — there's no sync between your phone and laptop, and clearing site data/browser history will wipe it. If you want it as your single source of truth across devices, deploying to GitHub Pages and always using it from the same browser (e.g. bookmarked on your phone) is the simplest way to keep it consistent. Export/import isn't built in yet, but would be a natural next addition if you outgrow single-device use.

## Tech

Vanilla HTML/CSS/JS, single file, no dependencies beyond Google Fonts (Oswald for display type, Work Sans for body text). No frameworks, no build step, nothing to install.
