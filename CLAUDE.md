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
├── CLAUDE.md                    ← you are here
├── REQUIREMENTS.md              ← full feature and content spec
├── index.html                   ← main site (single HTML file — everything lives here)
├── Basic_Bros_Logo.png          ← site logo (referenced directly in HTML)
├── site.webmanifest
├── BBRC Group Photo 2024.png    ← used in Tournament History section
├── BBRC Group Photo 2025.png    ← used in Tournament History section
├── Bro Pics/                    ← player profile photos (see section below)
│   ├── BovaPic.png
│   ├── CodyPic.png
│   ├── Donny2025.png
│   ├── JasonPic.png
│   ├── Karsten2025.png
│   ├── MuchaPic.png
│   ├── PletcherPic.png
│   ├── RaheemPic.png
│   ├── RynePic.png
│   ├── SchuPic.png
│   ├── SharkeyPic.png
│   ├── SpencerPic.png
│   └── TaylorPic.PNG
└── img/
    ├── Pawleys/                 ← hole photos for Pawleys Plantation (18 holes)
    └── Willbrook/               ← hole photos for Willbrook Plantation Golf Club (18 holes, pending)
```

**Stack:**
- Frontend: Single-file HTML + vanilla JS (no frameworks, no build step)
- Backend: Google Firebase **Realtime Database** — not Firestore (player bios, bio form submissions, tournament data). The site calls `firebase.database()`; there is no Firestore SDK loaded.
- Admin auth: Firebase Authentication (Email/Password), one commissioner account. The admin panel is gated by a real sign-in, and the database security rules only permit writes when signed in. Master copy of the rules lives in `database.rules.json` — keep it in sync with the Firebase console.
- Scoring data: Squabbit CSV export → admin upload panel (no public API exists)
- Hosting: DreamHost (static) — deploys automatically via GitHub Actions on every push to `main`
- Version control: GitHub (`https://github.com/bova4389/basic-bros-ryder-cup`)

**Deployment:**
- Push to `main` → GitHub Actions runs `.github/workflows/deploy.yml` → files upload to DreamHost via SFTP (port 22)
- A **"Stage deployable files"** step rsyncs the repo into `_deploy/` minus `CLAUDE.md`, `REQUIREMENTS.md`, `CLAUDE_AI_PHONE_CONTEXT.md`, `.github`, `.gitignore` and `*.pdf`; both upload steps read from `_deploy/`. Without it the action publishes everything tracked — `/CLAUDE.md` and `/REQUIREMENTS.md` used to be live on the domain. It is an exclude list, not an allow list, so a newly added photo still deploys without touching the workflow.
- DreamHost server path: `/home/mattbova/basic-bros-ryder-cup.com`
- GitHub secrets required: `FTP_SERVER`, `FTP_USERNAME`, `FTP_PASSWORD` (stored under Settings → Secrets → Actions)
- Uses `wlixcc/SFTP-Deploy-Action@v1.2.4` — DreamHost requires SFTP, plain FTP and FTPS do not work

**Cache Busting (Required — Do Not Remove):**
Safari on mobile caches pages aggressively. To prevent users from seeing stale versions after a deployment, this project has a `.htaccess` file that sends `no-cache` headers for all HTML, JS, and CSS. Never delete `.htaccess`. Since this project is a single HTML file with all styles/scripts inline, no `?v=` query strings are needed — the `.htaccess` alone is sufficient.

**Rules — do not change without asking:**
- Keep everything in one HTML file — no separate CSS or JS files
- No React, Vue, npm, or build tools
- All styles in `<style>`, all scripts in `<script>`
- Comment every meaningful code block in plain English
- Mobile-first — must work on phones without pinching or zooming
- CORS fallback chain for any API calls: direct → corsproxy.io → api.allorigins.win

---

## PLAYER PHOTOS

All player profile photos live in the `Bro Pics/` folder in the project root.

**How they wire up in the HTML:**
- Each `.player-card` element has a `data-photo="Bro Pics/filename.png"` attribute
- On page load, `swapPlayerAvatars()` reads that attribute and replaces the initials avatar with the photo
- The photo also displays in the full-screen bio modal via `openBioModal()`
- Players without a photo show their initials in a colored circle (green = GVO, purple = TI, gray = alumni)

**Naming convention:** `[FirstName]Pic.png` for standard shots, `[FirstName]YYYY.png` for year-specific photos (e.g. `Donny2025.png`).

**Adding a new photo:** Drop the file into `Bro Pics/`, then add `data-photo="Bro Pics/YourFile.png"` to the player's `.player-card` div in `index.html`.

---

## 2026 ROSTER STATE

**Good Vibes Only — Captain: Matt Bova ★**

| Player | Tier | Hdcp |
|---|---|---|
| Jason Damiani | T1 | 10 |
| Taylor Touchberry | T1 | 14 |
| Chris Schumann | T1 | 15 |
| Cody Esbrandt | T1 | 15 |
| Mitch Pletcher | T1 | 16 |
| Sebastian "Bash" Strobel | T1 | 16 |
| Joe Sharkey | T2 | 25 |
| Raheem Bishop | T2 | 26 |
| Joe Mucha | T2 | 26 |
| Matt Bova ★ | T2 | 26 |
| Spencer Schumann | T2 | 30 |
| Teddy Smith | T2 | 42 |

**Transfusion Intrusion — Captain: Adam Lewandowski ★**

| Player | Tier | Hdcp |
|---|---|---|
| Mike Davis | T1 | 3 |
| Renato | T1 | 11 |
| Robert Stephenson | T1 | 16 |
| Donny Bartlett | T1 | 17 |
| Ryne Stone | T1 | 18 |
| Mike Gaudet | T1 | 22 |
| Karsten Meyer | T2 | 24 |
| Max Harris | T2 | 26 |
| Ron Pannullo | T2 | 29 |
| Adam Lewandowski ★ | T2 | 35 |
| Jeremy Hermanson | T2 | 39 |
| Cassady Glenn | T2 | 41 |

**Alumni (not competing in 2026):**
Justin Reeves (2024–25), Johnny Pullman (2025), Jordan Partou (2024–25), Bennett Heath (2025), Stephen Burleson (2024), Jake Hammer (2025), Chris Schneider (2024–25), Mark Bowman (2025), Mike Gaudet (2025 — now active in 2026)

**Note on Justin Reeves:** Justin competed in 2024 and 2025 and may return in a future year. His 2024/2025 scores remain in the Tournament History data under his name. His player card is in the alumni section.

---

## SCRAMBLE HANDICAP FORMULA

For the Day 1 Scramble round, team handicap is calculated as:

**`round((player1_hdcp + player2_hdcp) × 0.35)`** — standard rounding (not ceiling)

Example: Mike Gaudet (22) + Hermanson (35) = 57 × 0.35 = 19.95 → **20**

This formula is confirmed against all 6 groups in the 2026 Day 1 pairings table.

---

## BRANDING & VISUAL IDENTITY

### Logo
`Basic_Bros_Logo.png` in the project root — do not hardcode assumptions about other asset paths.

### Color Palette (from logo)
- Dark navy/charcoal — primary background
- Forest green — accents, buttons, highlights
- Cream/ivory — primary text
- Gold/yellow — star accents, awards, highlights
- Red — flag detail, alert states

### Button Classes
- `.btn-primary` — green filled (main CTAs)
- `.btn-secondary` — gold outline (transparent background)
- `.btn-gold` — gold filled (used for The Bros homepage link to make it stand out)

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

## BIO SYSTEM

Player bios are submitted via a form and stored in Firebase. Approved bios are loaded on page load and injected into each player card.

**Card preview shows (in order):**
1. Known as (nickname) — only if different from the player's first name
2. Yearbook quote (truncated to 100 chars)
3. Fun fact (truncated to 100 chars)
4. "This person has no fun facts." — shown only if both yearbook quote AND fun fact are empty
5. "Show More" button → opens full-screen bio modal

**Full modal shows:** Known as, Hometown, Job, Family, Walk-up Song, Fun fact, Discord

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

---

## SESSION STARTER PROMPT TEMPLATE

> I'm building a golf league website called "Basic Bros Ryder Cup." Full requirements are in `REQUIREMENTS.md` and full context is in `CLAUDE.md`. Today I want to tackle [FEATURE NAME]. Read both files first, then present a plan before writing any code.
