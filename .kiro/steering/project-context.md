---
inclusion: auto
---

# Workout Tracker — Project Context

## Owner
- GitHub: dave-ciszewski
- Repo: https://github.com/dave-ciszewski/WorkOut
- Hosted: https://dave-ciszewski.github.io/WorkOut/
- Target device: iPhone (Safari, Add to Home Screen as PWA)

## Architecture
- Single file: `index.html` — no frameworks, no build tools, no dependencies
- All CSS inline in `<style>`, all JS inline in `<script>`
- Data stored in browser localStorage (key: `wt_v3`)
- State shape: `{s: startDate, dn: completedDays, ck: exerciseChecks, wt: weights/rounds/durations/reps, bw: bodyWeightLog, badges: earnedBadges, bestStreak: number, graduated: bool, goals: [{lbs, by}]}`

## Theme
- Default: OLED dark (#000 background, #1a1a1a cards, #f5f5f5 text)
- Light mode toggle available (stored in localStorage key `wt_mode`)
- Accent color: #4a9eff (blue)
- Designed for iPhone: safe area insets, big tap targets (32-44px), SF Pro font stack

## Weekly Schedule (Sun=index 0)
| Day | Type | Badge Class | Exercises | Special Tracking |
|-----|------|-------------|-----------|-----------------|
| Sunday | The Burner | db-b (orange) | KB Deadlifts 25lbs, Push-ups 12 reps (stepper), KB Snatches 25lbs, DB Thrusters 20lbs | Duration stepper (default 20m, 5m increments, max 60m), Round counter with last-week comparison |
| Monday | Walk | db-w (blue) | None | 45 Min Incline Walk, Zone 2 HR |
| Tuesday | Strength | db-s (pink) | KB Goblet Squats 25lbs, DB Shoulder Press 20lbs, KB Swings 25lbs, DB Renegade Rows 20lbs, Plank 60s (10s stepper) | Circuit stopwatch timer with last-week comparison |
| Wednesday | Walk | db-w (blue) | None | 30-45 Min Light Walk, Zone 1-2 HR |
| Thursday | Unilateral | db-u (purple) | Step-Ups 20lbs, KB Row 25lbs, DB Curl to Press 15lbs, Russian Twists 10lbs | Duration stepper (default 20m, 5m increments, max 60m) |
| Friday | REST / Make-up | db-r (green) | None | Shows missed days Sun-Thu as buttons; tapping credits both the missed day AND Friday |
| Saturday | Walk | db-w (blue) | None | 60 Min Incline Walk, High Zone 2 HR |

## Exercise Weight Defaults
- All KB exercises: 25lbs (user's kettlebell)
- DB Thrusters, DB Shoulder Press, DB Renegade Rows, Step-Ups: 20lbs
- DB Curl to Press: 15lbs
- Russian Twists: 10lbs
- All weights use 5lb increment steppers
- Push-ups: rep stepper (default 12, increment 1)
- Plank: seconds stepper (default 60, increment 10)
- All exercises have YouTube search links (▶️ icon) for form tutorials

## Goal Weights
- Goal 1: 190lbs by July 4, 2026
- Goal 2: 180lbs by October 31, 2026
- Shown in body weight expanded section with progress bars
- Editable in Settings, can add new goals
- Progress calculated from first logged weight to target

## Bi-Weekly Progressions (shown as milestone notes)
Weeks 2,4,6,8,10,12,14,16,18,20,22,24 each have a specific progression note displayed when viewing that week or later.

## Features Built (27 total)
1. **Stats bar** — 4 stats: Current Streak (orange), Best Streak (red, persists forever), Days Done (green), Current Week (blue)
2. **Body weight tracker** — Tap header to expand, log weight, shows delta from day 1, mini line chart with gradient fill
3. **Goal weight milestones** — Two goals with target dates, progress bars (green=on track, orange=past due), editable in Settings, can add more
4. **6-month progress bar** — Percentage based on elapsed days from start date
5. **Week navigator** — Browse weeks 1-26 with arrow buttons
6. **Day cards** — Expand/collapse, today auto-opens, color-coded badges per workout type
7. **Exercise checkboxes** — 32px tap targets, green when checked
8. **Weight steppers** — ±5lb per exercise, remembers last week's weight as placeholder
9. **Rep stepper** — Push-ups: default 12, increment by 1
10. **Time stepper** — Plank: default 60s, increment by 10s, displays as Xm Xs
11. **Round counter** — Sunday only, shows last week's count for comparison
12. **Duration stepper** — Sunday and Thursday, 5min increments, 5-60min range, default 20min
13. **Circuit timer** — Tuesday only, start/stop/reset stopwatch, shows last week's time
14. **Friday make-up** — Lists missed Sun-Thu days as buttons, credits both days on tap
15. **Calendar view** — Monthly grid, green=done, red=missed, gray=rest, blue outline=today
16. **Badges tab (🏆)** — 20 hidden badges, only earned ones shown (true easter eggs)
17. **Celebrations** — 30% random chance of fireworks + motivational quote on day complete
18. **Badge unlock modal** — Fireworks + badge reveal when earned
19. **Confetti rain for PRs** — Different from fireworks, triggers on: new best round count, fastest Tuesday time, new lowest body weight
20. **Graduation screen** — At day 182, fireworks + confetti + full stats summary (only once)
21. **Dark/light mode** — Toggle in header, persisted in localStorage
22. **Settings** — Visible date picker (iOS-friendly), goal weight editors with add/edit, export JSON, reset data
23. **20 motivational quotes** — Randomly shown in celebrations
24. **Walk rows** — Checkable with HR zone info
25. **YouTube exercise links** — ▶️ icon next to each exercise name, opens YouTube search for form tutorials
26. **Haptic feedback** — Light tap on steppers/checkboxes, heavy tap on day complete/makeup buttons
27. **Git integration** — Repo connected, pushes work from workspace via `git push origin main`

## 20 Badges
first_blood, week1, streak3, streak7, streak14, streak30, ten_done, twentyfive, fifty, hundred, month1, month3, month6, sunday_5, tuesday_5, walk_10, weight_up, early_bird, weekend_warrior, perfect_week

## Known Issues / Notes
- Git is installed and authenticated — pushes work from workspace via `git push origin main`
- Start date auto-adjusts to nearest Sunday (week always starts Sunday)
- The date picker was changed from hidden input to visible `<input type="date">` for iOS Safari compatibility
- Body weight input: the toggle click is on `.bw-top` only, not the whole `.bw-bar`, so the input field can receive focus on iOS. The input row has `event.stopPropagation()` to prevent collapsing.
- localStorage key is `wt_v3` — earlier versions (`workout_tracker_v1`, `wt_v2`) are abandoned
- Body weight chart uses canvas with devicePixelRatio scaling for retina displays
- `drawBWChart` uses hardcoded color `#4a9eff` instead of CSS variable (canvas limitation)
- Haptic feedback added to all interactive elements (light tap for steppers/checkboxes, heavy tap for day complete/makeup). Uses Vibration API + AudioContext fallback, but iOS Safari support is limited.
- iOS Safari quirks: hidden date inputs don't trigger picker, parent onclick handlers steal focus from child inputs
- Stepper functions (adj, adjR, adjDur, adjRep) must NOT call rW() or the open day card will collapse. They update DOM elements directly.
- To force refresh on iPhone: open URL directly in Safari, or clear Safari cache (localStorage data is preserved)

## Session Oct 30, 2026 — Revisit / Round 2 (PAUSED, resume here)
User goal: update + republish his version, then build a generic version for other users.

Environment: git is at `C:\Users\vcisdavi\AppData\Local\Programs\Git\cmd` and is NOT on PATH in the agent shell. Prefix commands with `$env:Path = "$env:LOCALAPPDATA\Programs\Git\cmd;$env:Path";`. Local main == origin/main (last commit a6df0b4, goal weights).

Data export: `workout-data Oct 30 2026.json` in workspace root (gitignored — contains personal body weight; never commit). Note: iPhone home-screen app and Safari have SEPARATE localStorage — export from whichever he logs in.

Key wt keys: `{date}_w{i}` weight, `_r{i}` reps/seconds, `_rnd` Sunday rounds, `_time` Tuesday seconds, `_dur` duration min. Exercise index i = position in SC[day].ex.

Findings from 6 months of data (Apr 26 – Oct 24, 2026):
- 135 days completed (incl. 11 Friday make-ups), best streak 91. Strong wks 5–19; dropped off from early Sept; last completed day Oct 17.
- Sunday rounds 3 → 4 (Aug on); often extended to 25–40 min. Wk14 goal (5 rounds) not met.
- Tuesday time: 31:18 first, best 23:57 (Aug 4), recent 24–30 min.
- Body weight 196.2 → low 190.0 (Sep 6) → 193.2 (Sep 27, last log). Goal 190 hit late; 180 not reached.
- Actual working weights he re-dialed every week: Push-ups 10, DB Thrusters 15, DB Shoulder Press 15, Renegade Rows 10, Step-Ups 15, Curl to Press 10, Russian Twists 15. KB moves stayed 25, Plank 60.

BUGS found:
1. Steppers do NOT carry forward — gWt() falls back to the hardcoded default each week; `lw()` exists but is unused. README claims carry-forward. Fix: default to most recent prior logged value.
2. `month6` (The Finisher) badge never awarded — checkBadges() only runs on tD/makeup, while checkGraduation runs on init. Fix: run checkBadges on init too.

Planned for his version (pending his routine changes): carry-forward fix, Finisher badge fix, "Start Round 2" (new start date/goals, keep history/badges/best streak), update exercise defaults to his actual weights, possibly the per-exercise graphs.

Open questions for other-users version: audience (friends on same plan vs anyone), what's configurable (start date, equipment weights, goals, exercises/schedule?), first-launch setup screen, hosting (recommended: subfolder `/app/` on main; alt: separate repo). MUST use a different localStorage key (same github.io origin).

UPDATE (end of Oct 30 session): Routine changes are DONE — but in a NEW app, not v1.
- User decided to KEEP v1 unchanged (root `index.html` restored to commit a6df0b4) and build a new version.
- New app: `v2/index.html` (copy of v1 with new routine). localStorage key `wt_v4` (fresh start, never touches `wt_v3`). Title "Workout Tracker v2", export file `workout-data-v2.json`.
- Routine source of truth: `v2/BLUEPRINT.md` (6-Month Master Workout Blueprint). Full session notes + earlier per-day drafts: `Session Notes Oct 30 2026.md`.
- v2 schedule: Sun Burner (Deadlifts, Push-ups 10, Snatches, Devil's Press 10 lb) + walk; Mon Recovery Walk; Tue Strength (Goblet Squat, 2-Hand High Pulls, DB Floor Press 15 lb, Swings, Plank); Wed Restorative/Yin Yoga (replaces walk, badge class db-y teal); Thu 25m Unilateral & Flow EMOM (Rev Lunge Pass-Through, SA KB Row, DB Push Press 15, Plank Pull-Throughs 10; 4 rounds × 5-min cycle = 20 min, duration default 20 — user corrected from 5 rounds on Oct 31); Fri rest; Sat Beach Run + Gym Backup (`alt` box).
- v2 new SC fields: `nt` (note under header), `pr` (collapsible progression box: title, intro, phases[{n, items, steps, stTitle, ol, post}]), `wx` (walk execution line), `wi` (walk icon), `alt` (backup cardio box). Shared `R4` constant = Rule of 4 text. PG milestones contain HTML (<b>).
- Nothing committed or pushed yet. v2 will be at /WorkOut/v2/ once pushed.

UPDATE Oct 31: Usability round 1 DONE in v2 (see v2/README.md "Usability features"). Data model now: exercise `id` on every SC exercise; wt keys `<date>_w_<id>`, `<date>_r_<id>`, ck `<date>_<id>`; Z.ph {sun,tue,thu}, Z.pt[date]={p,hit?}, Z.ls (Phase 3 load steps), Z.sat[date]='beach'|'gym', Z.phLog. Carry-forward via prevVal/valOf; snapshotDay on complete/make-up. PG milestones removed; pr box kept only for Wednesday. WL weight lists. openCards Set keeps cards open across rW(). Tested in headless Edge (Node not installed): `msedge --headless --dump-dom` only produces output via Start-Process -RedirectStandardOutput. Headless screenshots look clipped on the right — a viewport quirk, not a bug (verified scrollWidth == viewport).
v2 program set: 25 weeks, start Sun 2026-11-08 → end Sat 2027-05-01 (TD=175, NW=25, lastDay()/finished()). Goals 190 by 2027-01-01, 180 by 2027-04-30. Tuesday Phase 2 target (+2 reps: 14 squats / 12 floor press) confirmed by user.
PUSHED Oct 31 (commit dd11d22): v2 LIVE at https://dave-ciszewski.github.io/WorkOut/v2/ — v1 unchanged at /WorkOut/. User OK'd publishing chat/notes files (public repo).
Later Oct 31 additions (all in dd11d22): rep counters on every exercise (start at phase target, phRp/ru fields, no carry-forward for reps); warm-up block WU on Sun/Tue/Thu (reference list, no checkboxes; first move "Butt-Kicker Air Jump Rope"); R1 records const {streak:91,days:135} with pills + badges beat_r1_streak / beat_r1_days; Week One Down now fires at end of week 1 (weekOneDone); next-goal line in weight bar (goals show before first weigh-in); pick() no-repeat messages + DAY_MSGS; Saturday gym Option C stair climber; Thursday 4 rounds/20 min (Phase 3: 5 rounds/25 min via phase f/nt/dur overrides) + `rest` row; Sunday Phase 2 header "25 Min AMRAP"; Tue: KB Goblet Squat Curl, KB Deadlift to High Pull, Front Plank (R1&3) + Side Plank (R2&4); Sun: KB Swing Gorilla Deadlift + KB Suitcase Carry (hd 'After the AMRAP').
PUBLISHING RULE (v2): bump `const BUILD='YYYY-MM-DD.N'` in v2/index.html on EVERY push. The app fetches the live page (no-store) on open/return and reloads via ?v=<build> only if the live BUILD is newer (newerBuild) — once per build per session. Without a bump, iPhone home-screen app keeps the cached copy (GitHub Pages max-age=600). App Version is shown in Settings.
Next: user tries v2 on iPhone (Safari → Share → Add to Home Screen; separate from v1). Program starts Sun Nov 8, 2026. (warn: repo is public; chat/notes files contain personal info).

(Previous) Next step when resuming: USABILITY updates for v2 (see "Tomorrow" list in `Session Notes Oct 30 2026.md`): finer weight steps (1–2 lb), carry-forward fix, key weights by exercise not index, Finisher badge fix, decide on Wednesday Yoga Framework box, review default goals, then commit + push.

## Future Features (Revisit Later)
- Exercise progress graphs — mini sparkline charts per exercise showing weight/reps over time. Add after 4-6 weeks when there's enough data to be meaningful. Plan: small 📊 icon next to each exercise that expands a chart on tap.

## Files
- `index.html` — The entire app (v1, original routine — keep unchanged)
- `v2/index.html` — v2 app with the Master Blueprint routine (key `wt_v4`)
- `v2/BLUEPRINT.md` — v2 routine source of truth
- `v2/README.md` — v2 overview
- `Session Notes Oct 30 2026.md` — Oct 30 session notes, decisions, drafts, usability to-do
- `README.md` — Feature overview and setup instructions
- `.gitignore` — OS/editor/node ignores
- `.kiro/steering/project-context.md` — This file (auto-loaded every session)

## Hosting
- GitHub Pages from `main` branch, root folder
- Repo is public (free GitHub account requirement for Pages)
- User adds to iPhone home screen via Safari Share → Add to Home Screen
