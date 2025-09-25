<!--
Repository-specific instructions for AI coding agents.
Keep this short — ~20-50 lines — and focused on discoverable facts in the codebase.
-->

# Copilot instructions — Hello-World

Purpose: quickly orient an AI agent to be productive editing and running this repository (a small Next.js app using the App Router).

What this project is
- Next.js app (App Router) living in `src/app/` (server components by default). Key files:
  - `src/app/layout.tsx` — root layout, loads `next/font` (Geist) and `./globals.css`.
  - `src/app/page.tsx` — the main page; uses `next/image` and Tailwind utility classes.
- Static assets are in `public/` and are referenced by absolute paths (e.g. `/next.svg`, `/vercel.svg`).
- TypeScript is enabled (`tsconfig.json`, `next-env.d.ts`). Tailwind/PostCSS are present (`postcss.config.mjs`).

Quick developer workflows (discoverable from repo)
- Install deps: `npm install` (or `pnpm`/`yarn` if you prefer). The repo has no lockfile in this tree.
- Run dev server: `npm run dev` — this runs `next dev --turbopack` and serves at http://localhost:3000.
- Build: `npm run build` (uses `next build --turbopack`).
- Start production server: `npm run start` (runs `next start`).
- Lint: `npm run lint` (runs `eslint` — config is in `eslint.config.mjs`).
- Quick type-check (not in package.json): run `npx tsc --noEmit` to verify TypeScript without building.

Conventions & patterns to preserve
- App Router semantics: files under `src/app/` are route/layout components. Prefer server components unless `"use client"` is needed.
- Fonts are loaded with `next/font/google` and injected as CSS variables — preserve the variable names used in `layout.tsx` (e.g. `--font-geist-sans`, `--font-geist-mono`).
- Styling is Tailwind utility classes in TSX and global rules in `src/app/globals.css`.
- Images use `next/image` and reference the `public/` root (do not import SVGs as raw assets in these files).

Integration points & external services
- Designed for Vercel deployment (see README). No serverless/API routes are present in this snapshot.
- Build uses Next.js 15 and Turbopack flags in the scripts — expect different HMR behavior vs webpack.

Files to inspect when changing behavior
- `package.json` — scripts & deps
- `next.config.ts` — project configuration (currently empty/default)
- `eslint.config.mjs` — lint rules
- `postcss.config.mjs` and `src/app/globals.css` — CSS pipeline
- `src/app/layout.tsx`, `src/app/page.tsx` — main UI entry points
- `public/` — static assets referenced by pages

Editing guidance for an AI agent (concrete examples)
- If changing font usage: update `src/app/layout.tsx` where `Geist({ variable: "--font-geist-sans" })` and `Geist_Mono` are declared, and keep the same CSS variable names if you want existing CSS to continue working.
- If adding images, place them under `public/` and reference as `/your.png` in `next/image` (example: `src/app/page.tsx` uses `src="/next.svg"`).
- To experiment locally: run `npm run dev`, edit `src/app/page.tsx`, and observe HMR on save.

Notes / known gaps (what an agent should NOT assume)
- There are no test scripts or CI workflows in this tree — do not attempt to run tests unless you add them and update `package.json`.
- No API routes or backend services are present here; changes are front-end only in this snapshot.

If anything here is unclear or you want more detail (tests, CI, API routes, or deployment pipelines), tell me which area to expand and I will iterate.
