# TrainLog

A personal PWA workout tracker built for iPhone Safari. Single HTML file, no dependencies, no backend. AI-coached progressive overload training with full injury constraint awareness.

---

## Quick Start for Claude

When starting a new conversation, paste this + attach `index.html`:

> "Continuing TrainLog PWA development. Single HTML file, iPhone Safari, localStorage. My injury profile and full spec are in my memory profile. Phase 1 is complete. [Describe what you need]."

**Key files:**
- `index.html` — the entire app
- `README.md` — this file (context + changelog)
- `trainlog-spec.md` — full product specification

---

## Permanent Injury Constraints (never violate in any code or recommendation)

| Injury/Condition | Constraint |
|---|---|
| Left shoulder labrum repair (15yr ago) | NO overhead pressing ever |
| Right AC joint separation (Nov 2025) | Cable flies stop at shoulder parallel; lateral raises stop below shoulder height; no barbell bench, no dips |
| Bilateral Morton's neuroma | NO forefoot calf loading — seated calf raise only |
| Right GTPS | High foot plate on leg press mandatory; avoid deep hip flexion under load |
| Bilateral patellar tendinopathy | Mostly resolved — monitor |

---

## Architecture

- **Platform:** PWA, iPhone Safari primary
- **Hosting:** GitHub Pages
- **Structure:** Single `index.html` — no build process, no frameworks, no dependencies
- **Storage:** localStorage (`trainlog_v1`)
- **AI:** Anthropic API, `claude-sonnet-4`, called directly from browser
- **Sharing:** Each user forks the repo and hosts their own independent instance

---

## Current State: Phase 1 Complete

### What's built and working

- 4-session rotating minicycle (A/B/C/D) — not calendar week based (shift work schedule)
- Any session can be started in any order
- Session cards on home screen with expandable exercise preview
- Warmup checklists per session, skippable
- Exercise logging: weight / reps / RIR per set
- Add/remove sets freely
- Skip individual exercises with note
- Swap exercises mid-session
- Add custom exercises on the fly from library
- Progressive overload suggestions: 3% increase if goal met last session, flat if not
- Last session reference + estimated 1RM (Epley formula) displayed per exercise
- Post-session questionnaire: difficulty (1-5), fatigue (1-5), pain (0-10), pain exercise follow-up if >3, freehand notes
- AI coach check-in after every session — full injury context in system prompt
- Conversational AI follow-up
- Instant Workout builder — select muscle groups, get matching exercises
- Exercise library with 28 default exercises, muscle group tags, equipment category
- AI auto-fill for new exercises (primary/secondary muscles + coaching notes)
- Volume by muscle group chart (last 20 sessions)
- Estimated 1RM progress tracking
- Session history with expandable detail
- Calendar view — days with sessions highlighted
- localStorage persistence

### Known issues / limitations

- localStorage is unreliable in Claude artifact environment (WKWebView on iOS) — works correctly on GitHub Pages in Safari
- No export/backup yet (Phase 2)
- No mesocycle transitions yet (Phase 2)

---

## Phase 2 — Planned

- [ ] Mesocycle transitions — prompted at end of mesocycle (4-6 minicycles)
- [ ] AI plan builder — generates full plan based on injury profile + goals
- [ ] Plan creation/editing UI
- [ ] Muscle frequency view when building a plan
- [ ] Configurable progression rate (2–5%)
- [ ] Configurable minicycle size (3–5 sessions)
- [ ] Pain-based auto-adjustment recommendations
- [ ] Multiple saved plans with swap UI
- [ ] Export / backup functionality
- [ ] GitHub Pages deployment

---

## Phase 3 — Future

- [ ] Wrist roller / forearm tracking
- [ ] Deload week detection
- [ ] Body weight tracking
- [ ] Session duration tracking
- [ ] Mesocycle comparison charts

---

## Muscle Groups (22)

Chest, Front Delt, Side Delt, Rear Delt, Traps, Lats, Rhomboids, Serratus, Biceps, Triceps, Forearms, Abs, Obliques, Lower Back, Glutes, Hip Abductors, Hip Flexors, Adductors, Quads, Hamstrings, Calves, Tibialis

## Equipment Categories

Barbell, Dumbbell, Cable, Machine, Bodyweight, Band, Kettlebell

---

## Key Design Decisions

- **Plates-only logging on leg press** (sled weight ignored — machine-specific, irrelevant to progression)
- **Chest-supported row** = seated machine with chest pad, bilateral pull (not prone dumbbell)
- **High foot plate on leg press** is non-negotiable — eliminates trochanteric rubbing confirmed in testing
- **Chest fly ROM capped at shoulder parallel** — confirmed less AC joint pain at this ROM
- **Lateral raise hard stop below shoulder height** — above parallel causes AC impingement/clicking
- **No calendar week dependency** — minicycle rotates continuously regardless of days elapsed

---

## Changelog

### Phase 1 — Initial Build

- Full app shell with iPhone PWA support (safe area insets, add to home screen)
- Bottom navigation: Home, History, Charts, Library
- 4-session default plan (A/B/C/D) with warmups, exercises, sets/reps/RIR targets
- Exercise library with 28 pre-loaded exercises
- localStorage persistence
- Progressive overload engine (Epley 1RM, 3% progression, goal tracking)
- Post-session questionnaire + AI coach check-in
- Instant Workout builder
- Volume and 1RM charts
- Session history + calendar view

### Updates (post-initial build)

- Added warmup checklists to log screen with skip option
- Fixed session selection — all 4 sessions always tappable, not forced order
- Added "Next" badge to recommended session while keeping all sessions accessible
- Removed redundant "Next Up" card from home screen
- Added collapsible session summary panel in AI chat view
- Added auto-save draft with resume on reopen
- Switched storage attempts: localStorage → window.storage → back to localStorage (window.storage fails in iOS WKWebView/Claude artifact environment; localStorage is correct for GitHub Pages Safari deployment)
- Added visible save status indicator (✓ SAVED / SAVING... / ✗ SAVE FAILED)
- Added storage error banner with user guidance
- Confirmed: forefoot calf loading (leg press calf raises) worsens Morton's neuroma — removed from all sessions
- Confirmed: high foot plate on leg press eliminates trochanteric rubbing — hardcoded as mandatory
- Confirmed: chest fly ROM to shoulder parallel only — less AC joint discomfort
- Confirmed: lateral raises hard stop below shoulder height — above causes clicking/pain
- Clarified exercise: "Chest-Supported Row" = seated machine with chest pad (not prone)
- Machine Chest Press pain at 3-4/10 during session — stopped, not pushed through
- Complete app rebuild from scratch (cleaner architecture, better iPhone support)

---

## User Profile

- 41 years old, male
- 5 years training, intermediate-advanced
- 205 lb, ~14% BF
- Shift work schedule — irregular training days, minicycle structure preferred
- Science-based approach: progressive overload, full ROM, eccentric emphasis, proximity to failure
- Goals: hypertrophy, injury management, long-term progress
