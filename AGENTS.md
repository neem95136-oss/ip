# AGENTS.md — ระบบข้อบังคับการใช้มอด

## Overview
Single-page static HTML app (Thai military module regulations). All CSS and JS are inline in `index.html`. No backend, no database, no external API — fully client-side.

## Tech Stack
- **Vite** (dev server only) — serves `index.html` with live reload on port 3000
- No build step needed for dev; `index.html` is the entire app

## Running
```sh
docker compose -f docker-compose.base44.yml up -d
```
- Web entry: http://localhost:3000
- Vite dev server with file-watch polling (for bind-mount compatibility)
- Healthcheck probes `http://localhost:3000/`

## Structure
- `index.html` — the complete app (splash screen, 13 pages, bottom nav, AI chat, quiz, calculator, command checker)
- `package.json` — Vite dev dependency only
- `vite.config.js` — host 0.0.0.0, port 3000, polling watch
- `docker-compose.base44.yml` — node:22-slim, bind-mounted source, npm install on startup

## Key Features
- Splash screen with animated radar/loading sequence
- Pages: home, rules, law, allowed, banned, cheat, ai, menu, report, quiz, elig, calc, about
- Offline rule-based AI chat (no API needed)
- Command checker, punishment calculator, eligibility checker
- Dark/light theme toggle, sound effects, favorites (localStorage)
