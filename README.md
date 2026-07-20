# MCAT Simulator

A 1:1 full-length **MCAT practice exam simulator** with guided tutoring, subject-review lessons, spaced-repetition flashcards, and a performance dashboard. It runs entirely in the browser — no login, no backend — and works offline once loaded.

**Live:** https://isamy67.github.io/mcat-sim/

## Features

- **Exam Replica** — a full 1:1 simulation of the real MCAT: all four sections in the real order (Chem/Phys → CARS → Bio/Biochem → Psych/Soc), real break screens, section-locked navigation, a passage highlighter/strikethrough tool, flag-for-review, a question navigator, and an end-of-exam void decision. Produces an **estimated** scaled score (472–528). Sections can also be practiced individually, timed or untimed.
- **Tutor Mode** — the same questions, untimed, with step-by-step guided walkthroughs that teach how to attack each passage and eliminate wrong answers.
- **Learn** — AAMC-style written lessons organized by Foundational Concept (FC1–FC8) and the three CARS skill areas, each with a clinical-correlation callout.
- **Flashcards** — topic-tagged decks scheduled with the SuperMemo-2 (SM-2) spaced-repetition algorithm.
- **Performance Dashboard** — score trends, accuracy by section and by foundational concept, weak-area detection, and flashcard learning-stage stats.

> **Note on content:** all questions, passages, and lessons are original, written in the style/format/difficulty of AAMC material. Nothing is copied from real AAMC or UWorld content. Scaled scores are approximate estimates, not official AAMC-equated scores.

## Tech stack

- **Next.js** (App Router) + **TypeScript** + **Tailwind CSS v4**, exported as a fully static site (`output: 'export'`).
- **Zustand** state persisted to **IndexedDB** (attempts, results, tutor progress, flashcard scheduling).
- **Zod**-validated, content-file-driven data model — new exams, lessons, and decks are added as data, not code.
- **Vitest** unit tests for the timer, scoring, SM-2 scheduling, and dashboard analytics.

## Development

```bash
npm install
npm run dev        # http://localhost:3000
npm run test       # vitest
npm run build      # static export to ./out
```

## Deployment

Pushing to `main` builds the static export and deploys it to GitHub Pages via `.github/workflows/deploy.yml`. GitHub Pages must be enabled once for the repo (**Settings → Pages → Source = "GitHub Actions"**). The site is served under the `/mcat-sim` base path.
