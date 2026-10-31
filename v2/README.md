# 💪 Workout Tracker v2 — 6-Month Master Blueprint

A new version of the workout tracker built around the updated routine in [BLUEPRINT.md](BLUEPRINT.md). The original app (`/index.html` in the repo root) is untouched and keeps the original routine and all its history.

## How v2 differs from v1

- **Routine:** Sunday Burner with Devil's Press, Tuesday strength with Goblet Squat Curls / Deadlift to High Pulls / Floor Press, Wednesday Restorative Yoga (replaces walk), Thursday 20 min (4-round) Unilateral & Flow EMOM, Saturday Beach Run with Gym Backup.
- **Progression tracks:** Collapsible per-day boxes (Sunday, Tuesday, Thursday) showing the Rule of 4 and that day's Phase 1–3 targets.
- **Wednesday Yoga Framework box:** Duration guidance, tappable YouTube searches, and what to avoid.
- **Revised bi-weekly milestones** (Weeks 2–24) in the "Milestone This Week" banner.
- **Fresh start:** Uses its own localStorage key (`wt_v4`), so it starts with no history and never reads or overwrites v1 data (`wt_v3`). Export downloads `workout-data-v2.json`.

## Hosting

Lives in the `v2/` folder, so on GitHub Pages it will be at `https://dave-ciszewski.github.io/WorkOut/v2/` once pushed. Add it to the iPhone home screen separately from v1.

## Usability features (Oct 31, 2026)

- **Phase tracker** (Sun / Tue / Thu): each card shows your current phase, the exact target, and a "two in a row" progress meter. Sunday is checked automatically from rounds + duration; Tuesday and Thursday use a quick "Hit it / Not yet" tap. After 2 sessions in a row at target, a "Move to Phase N" button appears. Phase 3 shows a load-step checklist. "How progression works" explains all phases. Phases can also be set manually in Settings.
- **Phase-aware targets:** rep labels update with your phase (e.g. Thursday Phase 2 shows 12 lunges / 16 pulls), and Sunday's default duration follows the phase (20 / 25 / 20 min).
- **Weights carry forward** from your last logged session instead of resetting each week. Completing a day locks in the values shown.
- **Smarter weight steppers:** − / + step through real weights (DB: 5, 8, 10, 12, 15, 20…; KB: 5 lb steps). Tap the number to type any weight (rounds to 0.5 lb).
- **Logs keyed by exercise ID**, not list position, so reordering exercises never mixes up history.
- **Rep counters (− / +, steps of 1)** on every exercise. Reps start at the current phase's target each session (they don't carry forward); the number turns orange if you log below target. Weighted moves show reps under the name and weight on the right.
- **Warm-up** on Sunday, Tuesday, and Thursday: 6 moves × 30 sec, 2 rounds (~6 min), with form-video links. Reference only (no checkboxes); tap the header to collapse.
- **Round 1 records:** Best Streak and Days Done show your Round 1 marks (91-day streak, 135 days) underneath. Beat one and it changes to "🏆 Beat R1" and unlocks a badge: **Streak Breaker** (🔗) or **Volume Record** (📆). Values live in the `R1` constant.
- **Sunday duration** in 1-minute steps (Thursday stays at 5-minute EMOM cycles).
- **📊 Progress charts** for every exercise, Sunday rounds, and Tuesday circuit time.
- **Saturday Beach / Gym toggle**, with the gym options shown when Gym is picked.
- **Bi-weekly milestone banner removed.**
- **Fix:** The Finisher badge now unlocks (badges are checked on app open too).

- **Phone layout:** each exercise shows its name and form cue, then a compact controls row: **REPS** (or Reps / arm, Steps / side, Pulls total, Time) and **WEIGHT** side by side. The rep count appears only in the counter.
- **Routine updates (Oct 31):** Sunday KB Swing Gorilla Deadlift + post-AMRAP KB Suitcase Carry; Tuesday KB Goblet Squat Curl, KB Deadlift to High Pull, Front Plank (R1 & 3) / Side Plank (R2 & 4); Thursday 4 rounds (5 in Phase 3) with a Minute 5 rest row; Saturday gym Option C stair climber; warm-up on lifting days.
- **Auto-update:** the app checks for a newer `BUILD` on open and reloads itself (iPhone home-screen apps otherwise keep a cached copy). Current build shown in Settings → App Version. **Bump `BUILD` on every publish.**

## Program dates and goals

- **25 weeks:** Sunday Nov 8, 2026 → Saturday May 1, 2027 (`START_DEF`, `TD=175`).
- **Goals:** 190 lbs by Jan 1, 2027 · 180 lbs by Apr 30, 2027.
- Graduation triggers when May 1 is completed (or has passed).

## Status

Usability round 1 done (Oct 31, 2026). Remaining: set v2 goal weights, then commit + push.
