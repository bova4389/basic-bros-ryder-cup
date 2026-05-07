# CLAUDE.md — Basic Bros Ryder Cup

## WHAT THIS PROJECT IS

A fan-facing website for the **Basic Bros Ryder Cup** — an annual 3-day match play golf tournament among a group of ~24–30 guys, modeled after the real Ryder Cup format. The site serves as the official league hub: rules, player bios, tournament history, scoring, and course info.

**Owner/Commissioner:** Matt Bova (captain of Team "Good Vibes Only")
**Co-Founding Bros:** Cody Esbrandt, Ryne Stone
**Current Year:** 2026 — Pawleys Island, SC — June 25–28

---

## PROJECT STRUCTURE

```
basic-bros-ryder-cup/
├── CLAUDE.md              ← you are here
├── REQUIREMENTS.md        ← full feature and content spec
├── index.html             ← main site (single HTML file)
├── assets/
│   └── logo.png           ← Basic Bros Ryder Cup logo
└── README.md
```

**Stack:**
- Frontend: Single-file HTML + vanilla JS (no frameworks, no build step)
- Backend: Google Firebase Firestore (player bios, bio form submissions, tournament data)
- Scoring data: Squabbit CSV export → admin upload panel (no public API exists)
- Hosting: DreamHost (static)
- Version control: GitHub

**Rules — do not change without asking:**
- Keep everything in one HTML file — no separate CSS or JS files
- No React, Vue, npm, or build tools
- All styles in `<style>`, all scripts in `<script>`
- Comment every meaningful code block in plain English
- Mobile-first — must work on phones without pinching or zooming
- CORS fallback chain for any API calls: direct → corsproxy.io → api.allorigins.win

---

## BRANDING & VISUAL IDENTITY

### Logo
`assets/logo.png` — discover filename by directory listing, do not hardcode path.

### Color Palette (from logo)
- Dark navy/charcoal — primary background
- Forest green — accents, buttons, highlights
- Cream/ivory — primary text
- Gold/yellow — star accents, awards, highlights
- Red — flag detail, alert states

### Persistent Header
- "Basic Bros Ryder Cup" on every page
- Logo in header
- Light/dark mode toggle — persists via `localStorage`

### Responsive Design
- Mobile-first layout
- Tables scroll horizontally on small screens
- Navigation collapses on mobile
- All forms must be usable on a phone

---

## NAVIGATION STRUCTURE

Top-level tabs (in order):
1. **Home** — league overview, founding bros, quick links
2. **Rulebook** — full by-laws and special rules
3. **2026 Tournament** — current year (priority build)
4. **Tournament History** — 2024 (Year 1), 2025 (Year 2)
5. **Players** — bios, stats, career records
6. **Admin** — password-protected, CSV upload, bio approval

---

## SQUABBIT INTEGRATION — IMPORTANT

Squabbit (squabbitgolf.com) is the app used for live scoring and handicap tracking during the tournament. **There is no public API.**

**Claude Code first task on any scoring feature:** Before building any scoring UI, open browser dev tools on app.squabbitgolf.com and check the Network tab for undocumented API calls being made under the hood. If a usable endpoint exists, document it in this file and build against it. If not, proceed with the CSV upload approach.

**Fallback (CSV approach):**
- Admin downloads CSV export from Squabbit after each round
- Admin uploads CSV via the admin panel
- Site parses and displays results

**No manual score entry by Matt** — if there's no automated path, scores are post-event only. Do not build manual score entry forms.

---

## FIREBASE SETUP NOTES

Firebase is the backend for player bio submissions and tournament data storage. Matt is not deeply familiar with Firebase — provide step-by-step setup instructions whenever Firebase config is required.

**Every time Firebase setup is needed, Claude Code should:**
1. Tell Matt exactly what to do in the Firebase console (with screenshots described in plain English)
2. Identify where to find the config keys
3. Show exactly where to paste them in the HTML file
4. Test that the connection works before moving on

---

## HOW TO WORK ON THIS PROJECT

1. **Read CLAUDE.md and REQUIREMENTS.md first** before touching any code
2. **Present a written plan** of what you intend to build — wait for approval before coding
3. **Build one feature at a time** — complete and test before moving to the next
4. **Comment all code in plain English** — owner is not an engineer
5. **Test in browser** after every change
6. **Commit and push to GitHub** on completion of each working feature
7. **Never hardcode filenames** — use directory listings to discover asset names

---

## SESSION STARTER PROMPT TEMPLATE

> I'm building a golf league website called "Basic Bros Ryder Cup." Full requirements are in `REQUIREMENTS.md` and full context is in `CLAUDE.md`. Today I want to tackle [FEATURE NAME]. Read both files first, then present a plan before writing any code.
