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
- State shape: `{s: startDate, dn: completedDays, ck: exerciseChecks, wt: weights/rounds/durations/reps, bw: bodyWeightLog, badges: earnedBadges, bestStreak: number, graduated: bool}`

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

## Bi-Weekly Progressions (shown as milestone notes)
Weeks 2,4,6,8,10,12,14,16,18,20,22,24 each have a specific progression note displayed when viewing that week or later.

## Features Built
1. **Stats bar** — 4 stats: Current Streak (orange), Best Streak (red, persists forever), Days Done (green), Current Week (blue)
2. **Body weight tracker** — Tap to expand, log weight, shows delta from day 1, mini line chart with gradient fill
3. **6-month progress bar** — Percentage based on elapsed days from start date
4. **Week navigator** — Browse weeks 1-26 with arrow buttons
5. **Day cards** — Expand/collapse, today auto-opens, color-coded badges per workout type
6. **Exercise checkboxes** — 32px tap targets, green when checked
7. **Weight steppers** — ±5lb per exercise, remembers last week's weight as placeholder
8. **Rep/time steppers** — For bodyweight exercises (push-ups by 1, plank by 10s)
9. **Round counter** — Sunday only, shows last week's count for comparison
10. **Duration stepper** — Sunday and Thursday, 5min increments, 5-60min range
11. **Circuit timer** — Tuesday only, start/stop/reset stopwatch, shows last week's time
12. **Friday make-up** — Lists missed Sun-Thu days as buttons, credits both days on tap
13. **Calendar view** — Monthly grid, green=done, red=missed, gray=rest, blue outline=today
14. **Badges tab (🏆)** — 20 hidden badges, only earned ones shown (true easter eggs)
15. **Celebrations** — 30% random chance of fireworks + motivational quote on day complete
16. **Badge unlock modal** — Fireworks + badge reveal when earned
17. **Confetti rain for PRs** — Different from fireworks, triggers on: new best round count, fastest Tuesday time, new lowest body weight
18. **Graduation screen** — At day 182, fireworks + confetti + full stats summary (only once)
19. **Dark/light mode** — Toggle in header, persisted in localStorage
20. **Settings** — Visible date picker for start date (iOS-friendly), export JSON, reset data
21. **20 motivational quotes** — Randomly shown in celebrations
22. **Walk rows** — Checkable with HR zone info

## 20 Badges
first_blood, week1, streak3, streak7, streak14, streak30, ten_done, twentyfive, fifty, hundred, month1, month3, month6, sunday_5, tuesday_5, walk_10, weight_up, early_bird, weekend_warrior, perfect_week

## Known Issues / Notes
- Git not yet confirmed working on user's machine (winget install ran but may need PATH refresh or restart)
- Start date auto-adjusts to nearest Sunday (week always starts Sunday)
- The date picker was changed from hidden input to visible `<input type="date">` for iOS Safari compatibility
- localStorage key is `wt_v3` — earlier versions (`workout_tracker_v1`, `wt_v2`) are abandoned
- Body weight chart uses canvas with devicePixelRatio scaling for retina displays
- `drawBWChart` uses hardcoded color `#4a9eff` instead of CSS variable (canvas limitation)

## Files
- `index.html` — The entire app (~750 lines)
- `README.md` — Feature overview and setup instructions
- `.gitignore` — OS/editor/node ignores

## Hosting
- GitHub Pages from `main` branch, root folder
- Repo must be public (free GitHub account)
- User adds to iPhone home screen via Safari Share → Add to Home Screen
