# 💪 Workout Tracker v2 — 6-Month Master Blueprint

A new version of the workout tracker built around the updated routine in [BLUEPRINT.md](BLUEPRINT.md). The original app (`/index.html` in the repo root) is untouched and keeps the original routine and all its history.

## How v2 differs from v1

- **Routine:** Sunday Burner with Devil's Press, Tuesday strength with High Pulls / Floor Press, Wednesday Restorative Yoga (replaces walk), Thursday 25 min Unilateral & Flow EMOM, Saturday Beach Run with Gym Backup.
- **Progression tracks:** Collapsible per-day boxes (Sunday, Tuesday, Thursday) showing the Rule of 4 and that day's Phase 1–3 targets.
- **Wednesday Yoga Framework box:** Duration guidance, tappable YouTube searches, and what to avoid.
- **Revised bi-weekly milestones** (Weeks 2–24) in the "Milestone This Week" banner.
- **Fresh start:** Uses its own localStorage key (`wt_v4`), so it starts with no history and never reads or overwrites v1 data (`wt_v3`). Export downloads `workout-data-v2.json`.

## Hosting

Lives in the `v2/` folder, so on GitHub Pages it will be at `https://dave-ciszewski.github.io/WorkOut/v2/` once pushed. Add it to the iPhone home screen separately from v1.

## Status

Routine content done (Oct 30, 2026). Usability updates are next — see `.kiro/steering/project-context.md`.
