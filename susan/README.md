# 💪 Susan's Workout Tracker

Susan's version of the workout tracker: **all of v2's features** with **v1's exercises**, sized for her (15 lb kettlebells, 5–10 lb dumbbells, lower reps). Routine details: [ROUTINE.md](ROUTINE.md).

- **App:** `susan/index.html` → `https://dave-ciszewski.github.io/WorkOut/susan/` once pushed
- **Program:** 25 weeks, Sun Nov 8, 2026 → Sat May 1, 2027
- **Data:** own storage key `wt_susan_v1` — completely separate from Dave's v1 (`wt_v3`) and v2 (`wt_v4`). Export downloads `susan-workout-data.json`.
- **Goals:** none by default — Susan adds hers in Settings → Add Goal (starts 10 lbs under her latest weigh-in; editable).

## Susan-specific

- **Week layout:** Saturday is her rest / make-up day (Dave's is Friday); Friday is cardio.
- **Cardio machines:** Sun / Mon / Fri have an **Elliptical | StairMaster | Walk/Treadmill** toggle. Defaults: Sun Elliptical (30 min), Mon & Fri StairMaster (20 → 30 → 40 min with her Sunday phase). Wednesday is a walk (a Bambi walk counts).
- **🐕 Bambi walks (Susan's dog):** morning + afternoon minutes on every day with guidance (20–30 min each · 45 min a day). Total shows "25 / 45 min" and turns green ✅ at 45 (`DOG_GOAL`). 📊 chart; badges Bambi's Best Friend (50 walks), Pack Leader (200), Daily Dose (45 min on 30 days). Bonus only — doesn't affect streaks.

- **Personalized for "Suzie":** ~half of celebration titles use her name (SUZIE_TITLES), ~40% of messages are Suzie/Bambi-personal (SUZIE_MSGS), badge pop-ups say "Badge Unlocked, Suzie!" (SUZIE_BADGE_MSGS), graduation says "YOU GRADUATED, SUZIE!". Badges renamed: Suzie Starts Strong, Suzie the Burner Boss, Suzie Strong, Queen Suzie.

## Features (from v2)

Phase tracker (two in a row to advance, with "How progression works"), rep counters that start at each phase's target, weights that carry forward, tap-to-type weights, 📊 progress charts, warm-up on lifting days, next-goal line, badges (Week One Down at the end of week 1), varied motivational messages, compact phone layout, and auto-update (Settings → App Version).

## Not included (Dave-specific)

Round 1 record pills/badges, Dave's goals, v2's routine (Devil's Press, yoga, beach run / gym backup, Thursday rest row, suitcase carry, side plank).

## Publishing

Bump `const BUILD` in `susan/index.html` on every push so her phone auto-updates. Susan's app has its own build numbering.
