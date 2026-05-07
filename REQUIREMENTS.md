# REQUIREMENTS.md — Basic Bros Ryder Cup Website
*Read this file before writing any code. Last updated: May 2026.*

---

## WHAT THIS PROJECT IS

A public-facing league website for the **Basic Bros Ryder Cup** — an annual 3-day match play golf tournament. This is Year 3 (2026). The site is the permanent home for everything league-related: rules, rosters, player bios, course info, scoring, and history.

**Priority build order:**
1. Homepage
2. 2026 Tournament page (current year — most urgent before June 25)
3. Rulebook page
4. Players / Bio page + Bio submission form
5. Tournament History (2024, 2025)
6. Admin panel

---

## SECTION 1 — HOMEPAGE

### Content:
- Basic Bros Ryder Cup logo (prominent, centered or hero-style)
- Tagline / welcome blurb
- Quick-stat bar: Year (3rd Annual), Players (24), Location (Pawleys Island, SC), Dates (June 25–28, 2026)
- Founding Bros callout: **Matt Bova**, **Cody Esbrandt**, **Ryne Stone**
- Countdown timer to tournament start (June 25, 2026 — 9:03am ET)
- Quick links: View 2026 Tournament, Read the Rulebook, Player Bios
- Footer with contact: questions go to Founding Bros via Discord

### Design notes:
- Dark, premium feel — this is a prestige event to these guys
- Think Ryder Cup official site energy, not a rec league scorekeeper

---

## SECTION 2 — 2026 TOURNAMENT PAGE

### Sub-sections (use inner tabs or accordion):

#### 2a. Overview
- Tournament name: **2026 Basic Bros Ryder Cup**
- Dates: June 25–28, 2026
- Location: Pawleys Island, SC
- Lodging: Litchfield Golf and Beach Resort, 14276 Ocean Highway, Pawleys Island, SC 29585
- Condo assignments:
  - Condo 1: Spencer, Schumann, Ron, Jason, Max, Sharkey
  - Condo 2: Taylor, Donny, Bash, Raheem, Davis, Robert
  - Condo 3: Adam, Justin, Joe, Cass, Renato, Ryne
  - Condo 4: Bova, Mitch, Karsten, Teddy, Cody, Jeremy
- Prize fund: 1st place $225/player · 2nd place $75/player
- Entry fee: ~$900/player

#### 2b. Teams
**Team 1 — Good Vibes Only** (Captain: Matt Bova)

| Player | Tier | Handicap |
|---|---|---|
| Matt Bova | T2 | 28 |
| Chris Schumann | T1 | 16 |
| Spencer Schumann | T2 | 42 |
| Taylor Touchberry | T1 | 12 |
| Sebastian "Bash" Strobel | T1 | 16 |
| Teddy Smith | T2 | 42 |
| Jason Damiani | T1 | 12 |
| Raheem Bishop | T2 | 26 |
| Joe Mucha | T2 | 26 |
| Mitch Pletcher | T1 | 15 |
| Joe Sharkey | T2 | 22 |
| Cody Esbrandt | T1 | 16 |

**Team 2 — Luben Dubers** (Captain: Adam Lewandowski)

| Player | Tier | Handicap |
|---|---|---|
| Adam Lewandowski | T2 | 34 |
| Jeremy Hermanson | T2 | 35 |
| Donny Bartlett | T1 | 19 |
| Ron Pannullo | T2 | 30 |
| Mike Davis | T1 | 3 |
| Robert Stephenson | T1 | 14 |
| Justin Reeves | T1 | 20 |
| Ryne Stone | T1 | 18 |
| Cassady Glenn | T2 | 44 |
| Renato | T1 | 11 |
| Karsten Meyer | T2 | 24 |
| Max Harris | T2 | 26 |

#### 2c. Schedule / Itinerary
- **Thursday June 26** — 4:00pm Check-in. 7:00pm Team Meeting. 7:30pm 2027 Captain Selections.
- **Friday June 27** — 9:03am first tee (Pawleys Plantation). PM: Saturday matchup selection + 2027 date/location discussion.
- **Saturday June 28** — 7:57am first tee (True Blue Golf Club). PM: Sunday matchup selection.
- **Sunday June 29** — 8:06am first tee (Caledonia Golf & Fish Club). Final round. Scores tallied at clubhouse bar. Putt-off if tied.

#### 2d. Courses

**Friday — Pawleys Plantation**
- Address: 70 Tanglewood Dr., Pawleys Island, SC 29585
- Tees: Red
- Par 72 | Rating: 70.6 | Slope: 133
- First tee: 9:03am

**Saturday — True Blue Golf Club**
- Address: 900 Blue Stem Dr., Pawleys Island, SC 29585
- Tees: White
- Par 72 | Rating: 62.7 | Slope: 111
- First tee: 7:57am

**Sunday — Caledonia Golf & Fish Club**
- Address: 369 Caledonia Dr., Pawleys Island, SC 29585
- Tees: Mallard
- Par 70 | Total: 6,121 yards
- First tee: 8:06am

Display each course with: name, address, tees played, par, yardage, Google Maps link.
Include course scorecard data (hole-by-hole par/yardage) if layout allows — this data is in the PDF program.

#### 2e. Round 1 Pairings (Scramble — Friday)
Format: T1 + T2 vs T1 + T2. Handicap = 35% of combined total, rounded UP.

| Team Luben Dubers | HDCP | vs | Team Good Vibes Only | HDCP |
|---|---|---|---|---|
| Ryne (18) + Karsten (24) | 15 | vs | Cody (15) + Sharkey (22) | 13 |
| Cass (44) + Renato (11) | 19 | vs | Taylor (12) + Joe M (26) | 13 |
| Davis (3) + Adam (34) | 13 | vs | Mitch (15) + Raheem (26) | 14 |
| Justin (20) + Hermanson (35) | 19 | vs | Jason (12) + Bova (28) | 14 |
| Donny (19) + Max (26) | 16 | vs | Bash (16) + Spencer (42) | 20 |
| Robert (14) + Ron (30) | 15 | vs | Schumann (16) + Teddy (42) | 20 |

#### 2f. Scoring / Live Results
**⚠️ Important build note:** Squabbit has no public API. Claude Code must first inspect Squabbit's network traffic in dev tools to check for an undocumented API. If found, build against it. If not, implement a CSV upload flow in the Admin panel.

Display for each round:
- Match results (W/L/T per pairing)
- Points earned per match
- Running team totals
- First to 36.5 points wins

Points available: Day 1 = 12 · Day 2 = 24 · Day 3 = 36 · Total = 72

---

## SECTION 3 — RULEBOOK PAGE

Display the full By-Laws in clean, readable format. Content is sourced from `Basic_Bros_Ryder_Cup_By-Laws.pdf`. Use section headers and accordions or tabs for readability.

Sections to include:
1. General Items & Course Selection
2. Fees & Payments
3. Requirements
4. Format (Day 1 Scramble, Day 2 Singles, Day 3 Pods/Doubles+Singles)
5. Scoring System + Tie-Breaker
6. Captains & Teams
7. Handicaps (Squabbit-based, USGA rules, max 45, round UP)
8. Players
9. Injuries / Anomalies
10. Special Playing Rules (Clean & Replace, Double Par, Mulligans, OB, Weather)
11. Special Clauses (the fun ones — "Be a basic bro, not a basic bitch")

---

## SECTION 4 — PLAYERS PAGE

### 4a. Player Cards (display)
Each player card shows:
- Photo (uploaded via bio form or placeholder avatar)
- Name
- Current handicap
- Tier (T1 or T2)
- Years participated
- Career BBRC record (W / L / T)
- Fun facts / bio blurb (from bio form)
- Hometown / where they live

### 4b. Career Stats table
Columns: Player | Years | Matches Played | W | L | T | Win % | Points Contributed | Best Finish

Note: Year 1 (2024) data is limited — only 1 round, 12 players, handicaps were rough estimates. Mark Year 1 stats with a disclaimer footnote.

### 4c. Player Bio Submission Form
This is how Matt collects info from the ~30 guys. Must be:
- Mobile-friendly (guys will fill this out on their phones)
- Simple and fast — not a long survey
- Submitted to Firebase

**Form fields:**
- First & Last Name (required)
- Preferred display name / nickname (optional)
- Hometown / where you live now (required)
- Occupation (optional)
- Family status (e.g., "Married, 2 kids") (optional)
- Years participated in BBRC (required)
- Favorite golf course you've ever played (optional)
- Best golf moment / story (optional — 1-2 sentences)
- Fun fact about yourself (optional)
- Profile photo upload (optional — mobile camera-friendly)
- Squabbit username (required — for linking scoring data)
- Submit button

After submission: show confirmation message. Admin reviews in admin panel before publishing to Players page.

---

## SECTION 5 — TOURNAMENT HISTORY

### Year 1 — 2024
- Format was slightly different: 1 round only, 12 players
- Handicaps were not well-established
- Note this context prominently on the page
- Data source: Squabbit CSV (need admin to export and provide)

### Year 2 — 2025
- Full 3-day format
- 24 players
- Data source: Squabbit CSV

### Each year displays:
- Winner (team name + captain)
- Final score
- MVP / high points earner (if available)
- Course(s) played
- Memorable moments (can be added manually later)

---

## SECTION 6 — ADMIN PANEL

Password-protected. Single admin password stored hashed in Firebase.

### Features:

#### 6a. CSV Score Upload
- Upload Squabbit CSV export for any round
- Site parses and maps players to match results
- Preview before publishing
- Publish to live scoring display

#### 6b. Bio Submissions Manager
- View all pending player bio submissions
- Approve → publishes to Players page
- Edit any field before approving
- Reject / delete

#### 6c. Tournament Manager
- Mark tournament as active or complete
- Edit team rosters and handicaps
- Update matchup pairings for Rounds 2 and 3 (assigned night before each round)

#### 6d. Firebase Setup (first-time only)
When Claude Code builds the admin panel, include step-by-step Firebase setup instructions:
1. Go to console.firebase.google.com
2. Create a new project named "basic-bros-ryder-cup"
3. Add a web app — copy the config snippet
4. Enable Firestore database (start in test mode)
5. Paste config into the HTML file in the marked location
6. Test connection before proceeding

---

## DESIGN SYSTEM

### Colors (CSS variables)
```css
--color-bg: #0f1923;          /* dark navy */
--color-surface: #1a2535;     /* slightly lighter navy */
--color-green: #2d6a4f;       /* forest green */
--color-green-light: #52b788; /* lighter green accent */
--color-cream: #f5f0e8;       /* ivory text */
--color-gold: #d4af37;        /* gold accents */
--color-red: #c0392b;         /* red flag / alerts */
--color-muted: #8899aa;       /* secondary text */
```

### Typography
- Display/headers: a bold serif or slab font — premium, trophy-case feel
- Body: clean, readable sans-serif
- No Inter, Roboto, or Arial

### Component Patterns
- Cards with subtle border + shadow
- Tabs with active indicator in green
- Tables with alternating row shading, horizontal scroll on mobile
- Buttons: green primary, gold secondary
- Badges for Tier 1 / Tier 2 designation

---

## RESOLVED DECISIONS

| Topic | Decision |
|---|---|
| Squabbit API | No public API. Check for undocumented API first; fallback is CSV upload. |
| Live scoring | Only possible if undocumented API found. Otherwise post-round only. |
| Bio collection | Custom form in site → Firebase. Mobile-friendly. |
| Backend | Firebase Firestore |
| Hosting | DreamHost (static files) |
| Repo | New GitHub repo: `basic-bros-ryder-cup` |
| Single file | Yes — one index.html, all CSS/JS inline |
| Year 1 data | Limited — 1 round, 12 players, rough handicaps. Mark with disclaimer. |

---

## HOW TO WORK ON THIS PROJECT

1. **Read CLAUDE.md and REQUIREMENTS.md first** — every session
2. **Present a plan before coding** — no surprise rewrites
3. **Build in priority order** — Home → 2026 Tournament → Rulebook → Players → History → Admin
4. **Comment all code in plain English**
5. **Test in browser after every change**
6. **Commit to GitHub after each completed feature**
7. **Flag any payout math or scoring edge cases** — don't assume
8. **Never hardcode asset filenames** — use directory listing to discover
