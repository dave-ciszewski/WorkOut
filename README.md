# 💪 6-Month Workout Tracker

A mobile-first PWA for tracking a 6-month weight loss workout program. Built as a single HTML file — no frameworks, no build tools, no server required.

## Features

- **Weekly Schedule** — Sunday (AMRAP), Monday (Walk), Tuesday (Strength), Wednesday (Walk), Thursday (EMOM), Friday (Rest/Make-up), Saturday (Walk)
- **Exercise Tracking** — Check off exercises, log weights with 5lb steppers, track reps for bodyweight moves
- **Round Counter** — Track AMRAP rounds on Sunday with week-over-week comparison
- **Circuit Timer** — Stopwatch for Tuesday strength circuits with previous week's time displayed
- **Duration Stepper** — Adjustable workout duration for Sunday and Thursday (5min increments, up to 60min)
- **Body Weight Tracker** — Log daily weight with a trend chart from day 1
- **6-Month Progress Bar** — Visual progress from start date to finish
- **Streak Tracking** — Current streak + all-time best streak that persists forever
- **Friday Make-up Day** — Pick a missed workout from the week to credit
- **Bi-Weekly Progression Milestones** — Automatically shown based on current week
- **Calendar View** — Color-coded monthly view (green=done, red=missed, gray=rest)
- **Dark/Light Mode** — Toggle for gym vs outdoor lighting
- **20 Hidden Badges** — Easter egg achievements unlocked by working out
- **Celebrations** — Random fireworks + motivational quotes on day completion
- **Confetti for PRs** — Special animation for new round records, fastest circuits, or lowest body weight
- **Graduation Screen** — Full celebration at Week 26 with total stats summary
- **Data Export** — Download all data as JSON
- **Offline Ready** — All data stored in localStorage on your device

## Setup

1. Upload `index.html` to a GitHub repo
2. Enable GitHub Pages (Settings → Pages → Deploy from main branch)
3. Open the URL on your iPhone in Safari
4. Tap Share → "Add to Home Screen"

## Tech

Single HTML file. Vanilla JS. No dependencies. ~750 lines.
