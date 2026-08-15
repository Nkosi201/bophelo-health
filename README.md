# KasiCare (Bophelo Healthcare)

A community healthcare companion app: digital health card, nearby clinics, and a simple health assistant chat ("Nompilo").

Built from your uploaded shadcn/ui component kit + `AppShell`/`kasicare.ts` data layer, wired up as a complete, runnable **Vite + React + TypeScript + Tailwind** project.

## Run it in VS Code

1. Open this folder in VS Code.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the dev server:
   ```bash
   npm run dev
   ```
4. Open the printed local URL (usually `http://localhost:5173`).

## Build for production

```bash
npm run build
npm run preview
```

## Project structure

```
src/
  components/
    ui/            shadcn/ui primitives (from your upload)
    AppShell.tsx   bottom-nav app shell (adapted to react-router-dom)
  pages/
    CardPage.tsx       digital health card ("/")
    ClinicsPage.tsx    nearby clinics list ("/clinics")
    NompiloPage.tsx    health assistant chat ("/nompilo")
  lib/
    kasicare.ts    demo data + localStorage-backed hooks (from your upload)
    utils.ts       cn() helper (from your upload)
  hooks/
    use-mobile.tsx (from your upload)
  App.tsx          route definitions
  main.tsx         entry point
  index.css        Tailwind + design tokens (warm teal healthcare theme)
```

## Notes on what changed from your upload

- The zip contained only the **UI component library**, `AppShell.tsx`, and `kasicare.ts` — no `package.json`, build config, router setup, or page content. This project adds all of that.
- `AppShell.tsx` originally used `@tanstack/react-router`. It's been adapted to use `react-router-dom` instead, since that's simpler to run standalone. If you'd rather use TanStack Router/Start, that's a straightforward swap.
- All three pages your bottom nav points to (Card, Clinics, Nompilo) were built to match the data already defined in `kasicare.ts` (patient info, clinics).
- Data (appointments) persists to `localStorage` in the browser, as set up by the original hooks.
- `resizable.tsx` and `skeleton.tsx` had small import bugs (missing `React` import, wrong `react-resizable-panels` export names) — fixed so the whole kit type-checks and builds cleanly.
- Nompilo's replies are simple keyword-based canned responses (no AI API call) — easy to swap for a real API call to Claude or another LLM if you want it to be smarter.
