# Session Notes — Oct 30, 2026: Routine Update (v2)

## What we did

1. Exported the original routine as plain text for Google.
2. Worked through each day of the week to build a new routine and progression plan.
3. Consolidated everything into the **6-Month Master Workout Blueprint** (see `v2/BLUEPRINT.md` — the final source of truth).
4. Built the new routine into a **separate v2 app** (`v2/index.html`). The original app (`index.html`) was restored to its last commit and is unchanged.

## Decisions

- **Keep v1 as-is.** Old routine and 6 months of history stay in the original app.
- **v2 starts fresh.** Separate storage key `wt_v4` (v1 uses `wt_v3`), so no shared or overwritten data. Title shows "Workout Tracker v2".
- **Wednesday:** Restorative / Yin Yoga *replaces* the walk (not added to it).
- **Saturday:** Beach run is primary; gym backup (elliptical / bike) shown in a collapsible box. One checkbox counts either.
- **Progression track** is shown per day (Sun / Tue / Thu boxes each show the Rule of 4 + that day's Phase 1–3), rather than one combined block.
- **Wednesday Yoga Framework box** kept in v2 even though it isn't in the final blueprint — open question whether to keep it.
- **Old bi-weekly milestones** replaced with the revised Week 2–24 tracker.

## Tomorrow: usability updates (ideas raised so far)

- Finer weight steps (currently 5 lb only — can't select 12 lb for Devil's Press / Push Press).
- Weights carry forward from the last logged week instead of resetting to the default each week (known bug: `gWt()` ignores history; `lw()` exists but is unused).
- Store weights by exercise identity instead of list position (changing exercise order remaps old logs).
- Finisher (`month6`) badge never awards — run `checkBadges()` on init.
- Decide whether to keep the Wednesday Yoga Framework box.
- Review default goals in v2 (still 190 by Jul 4 and 180 by Oct 31, 2026 — both dates now past/at hand).
- Optional: phase tracker (mark which phase you're in per day).
- Then: push to GitHub so v2 is live at `/WorkOut/v2/` (not pushed yet; nothing committed).

---

## Earlier per-day drafts (superseded by the blueprint, saved for reference)

### Sunday draft

SUNDAY – THE BURNER (20 min AMRAP)
- KB Deadlifts – 15 reps – 25 lbs
- Push-ups – 10 reps
- KB Snatches – 8 reps / arm – 25 lbs
- DB Devil's Press – 10 reps – 10–12 lbs
- Then: 45 Min Incline Walk – Zone 2 to Low Zone 3

SUNDAY AUTOREGULATED PROGRESSION TRACK
- **Phase 1: The 4-Round Speed Milestone (20-Min Cap)**
  - Weight Strategy: Keep KB at 25 lbs, DBs at 10–12 lbs.
  - Focus: Minimize transition times between the four movements.
  - Progress Marker: Advance once you can complete 4 full rounds in 20 minutes with perfect form.
- **Phase 2: The 5-Round Density Milestone (25-Min Cap)**
  - Weight Strategy: Keep KB at 25 lbs, DBs at 10–12 lbs.
  - Focus: Extend the workout window to handle higher training volume.
  - Progress Marker: Advance once you can complete 5 full rounds in 25 minutes.
- **Phase 3: The Horizon Strength Milestone (35 lbs)**
  - Weight Strategy: Introduce the 35 lb kettlebell.
  - Focus: Drop time cap back to 20 minutes to manage the heavier load.
  - Safe Load Progression Steps:
    1. Use the 35 lb KB for Deadlifts only (keep Snatches at 25 lbs).
    2. Move Snatches to the 35 lb KB once shoulder stability feels locked in.
    3. Gradually scale up Devil's Press dumbbells from 12 lbs toward 15–20 lbs.

### Monday draft

Monday stays the same: 45 Min Incline Walk – Solid Zone 2.

### Tuesday draft

TUESDAY – STRENGTH (4 Rounds)
- KB Goblet Squats – 12 reps – 25 lbs (Include a strict 2-sec pause at the bottom)
- Two-Handed KB High Pulls – 12 reps – 25 lbs
- DB Floor Press – 10 reps – 20 lbs (Use a 4-sec lowering phase + 1-sec dead stop at the bottom)
- KB Swings – 20 reps – 25 lbs
- Plank – 60 sec
- Rest 60 seconds between rounds. Keep it active with a light step-touch or boxer bounce to maintain your fat-burning state.

TUESDAY AUTOREGULATED PROGRESSION TRACK

The Rule of 4: You only advance your weight when you can hit the target reps across ALL 4 rounds with perfect form and the required tempos. If form breaks on Round 3 or 4, keep the weight the same next week.

1. **KB Goblet Squats (Target: 12 Reps)**
   - When to move up: When you hit 12 reps with the 2-sec pause at the bottom across all 4 rounds.
   - The Next Step: Swap your 25 lb KB for the 35 lb KB. Drop your starting target down to 8 reps, and slowly build your volume back up to 12 reps over the weeks.
2. **Two-Handed KB High Pulls (Target: 12 Reps)**
   - When to move up: When you can complete 12 explosive pulls to collarbone height with high elbows across all 4 rounds.
   - The Next Step: Advance to the 35 lb KB. Drop your target to 8 reps to adjust to the heavier pull.
3. **DB Floor Press (Target: 10 Reps)**
   - When to move up: When you can complete 10 reps across all 4 rounds while strictly maintaining the 4-second descent and the 1-second dead stop on the floor.
   - The Next Step: If you have access to heavier dumbbells, move up to 25 lbs and drop your target to 6–8 reps. If restricted to 20 lbs, elevate your hips into a strict glute bridge position to increase muscular demand.
4. **KB Swings (Target: 20 Reps)**
   - When to move up: When you complete 20 powerful, sharp hip snaps to chest height across all 4 rounds.
   - The Next Step: Upgrade to the 35 lb KB. Drop your volume target down to 12–15 reps to safely manage the new load.

### Wednesday draft (yoga rationale)

Yoga for Wednesday, used for deep recovery rather than a strenuous workout. Tuesday's routine heavily loads the chest, hamstrings, and upper back, so a fast-paced power yoga class would overload those same muscles. A restorative routine supports recovery and the weight loss goal by lowering stress, resetting the nervous system, and opening up stiff joints.

The Wednesday Yoga Framework
- **The Sweet-Spot Duration:** 20 to 30 minutes maximum. Anything past 30 minutes shifts the body out of recovery mode and starts creating new muscular fatigue.
- **The Target Keywords to Search Online:** "Yin Yoga," "Restorative Yoga," "Yoga for Sore Muscles," or "Deep Stretch for Athletes."
- **What to Avoid:** "Vinyasa," "Power Yoga," or "Flow" classes with lots of planks and chaturangas (push-up movements), which would over-fatigue the chest after Tuesday's floor presses.

Decision: yoga **replaces** the Wednesday walk.

### Thursday draft

THURSDAY – UNILATERAL & FLOW INTERVALS (25 Min Total)

Perform the designated reps at the start of each minute, rest for the remainder of that minute, and take a full mandatory rest on Minute 5. Repeat for 5 total rounds.
- Minute 1: KB Reverse Lunge Pass-Through – 10 total lunges (5 / leg) – 25 lbs
- Minute 2: Single-Arm KB Rows – 10 reps / arm – 25 lbs
- Minute 3: DB Push Press – 10 reps – 12–15 lbs (Slight knee dip-and-drive)
- Minute 4: DB Plank Pull-Throughs – 12 total pulls – 10 lbs
- Minute 5: MANDATORY RESET – Full 60 Seconds of Complete Rest

THURSDAY AUTOREGULATED PROGRESSION TRACK

The Rest-Buffer Rule: You only unlock a progression phase when you can complete all 5 rounds of the EMOM while strictly maintaining a minimum 15-second rest window at every active station (Minutes 1–4).

- **Phase 1: The Pacing Floor (Current Baseline)**
  - Weight Strategy: Keep weights at Reverse Lunges (25 lbs), KB Rows (25 lbs), Push Press (12–15 lbs), and Plank Pull-Throughs (10 lbs).
  - The Marker: Focus on smooth coordination and balance. When you can survive all 25 minutes without your active rest windows shrinking below 15 seconds, advance to Phase 2.
- **Phase 2: The Rep Escalation Track (+2 Reps)**
  - Weight Strategy: Keep the starting weights exactly the same.
  - The Marker: Increase the volume density inside each minute to drive up your metabolic conditioning and support your 180 lb target:
    - KB Reverse Lunges: Push to 12 total lunges (6 / leg)
    - Single-Arm KB Rows: Push to 12 reps / arm
    - DB Push Press: Push to 12 reps
    - DB Plank Pull-Throughs: Push to 16 total pulls
  - Advance once you can successfully complete all 5 rounds at this higher rep volume while keeping your form pristine.
- **Phase 3: The Weight Jump (Load Step)**
  - Weight Strategy: Reset all your rep targets completely back down to the baseline 10 reps (12 total pulls for pull-throughs) and step up your load across the board:
    - KB Rows: Upgrade to your 35 lb KB.
    - DB Push Press: Upgrade to 20 lbs.
    - DB Plank Pull-Throughs: Upgrade to 12–15 lbs.
    - KB Reverse Lunges: Upgrade to your 35 lb KB (or drop reps back to 10 total if using the 25 lb KB with a strict 2-second pause at the bottom).

### Weekly cardio log draft

**SUNDAY – THE POST-BURNER FLUSH**
- Workout: 45 Min Incline Walk (Performed immediately after your lifting AMRAP)
- Intensity: Zone 2 leading into Low Zone 3
- Execution: Let your heart rate climb naturally into Low Zone 3 during the second half of the walk as fatigue sets in from the weights to maximize late-stage fat burning.

**MONDAY – STEADY-STATE RECOVERY**
- Workout: 45 Min Incline Walk
- Intensity: Strict, Solid Zone 2
- Execution: Keep your pacing smooth, controlled, and comfortable to flush out your lower body from the weekend.

**WEDNESDAY – ACTIVE RECOVERY RESET**
- Workout: 20–30 Min Restorative / Yin Yoga Routine (Online Search)
- Intensity: Passive Floor Stretching (Zero Strain)
- Execution: Focus on slow, deep breathing and holding floor stretches to open up your chest, shoulders, and hips. Avoid any classes with power movements, planks, or push-ups.

**SATURDAY – THE AEROBIC ENGINE (PRIMARY OPTION)**
- Workout: 30–45 Min Continuous Beach Run (No Intervals)
- Intensity: Strict Zone 2 Target
- Execution: Run continuously on the wet, packed sand near the water line. Keep your speed at a steady, rhythmic jog where you can comfortably breathe entirely through your nose.

**SATURDAY – THE GYM BACKUP (WEATHER / LOGISTICS OPTION)**
- Workout: 30–45 Min Continuous Pacing (No Intervals)
- Intensity: Strict Zone 2 Target
- Option A (Elliptical Trainer): Set resistance to a medium level (6–10), keep incline low or flat, and maintain a smooth, steady gliding pace.
- Option B (Stationary Upright Bike): Set resistance high enough that you push firmly with your heels on every stroke, maintaining a steady cadence of 80+ RPM.

---

## Original routine (v1, unchanged)

SUNDAY – THE BURNER (20 min AMRAP): KB Deadlifts 15 reps 25 lbs · Push-ups 12 reps · KB Snatches 8/arm 25 lbs · DB Thrusters 12 reps 20 lbs · Then 45 Min Incline Walk (Zone 2 – Low Zone 3)
MONDAY – WALK: 45 Min Incline Walk (Solid Zone 2)
TUESDAY – STRENGTH (4 Rounds): KB Goblet Squats 12 reps 25 lbs · DB Shoulder Press 10 reps 20 lbs · KB Swings 20 reps 25 lbs · DB Renegade Rows 10/side 20 lbs · Plank 60 sec
WEDNESDAY – WALK: 30–45 Min Light Walk (Zone 1 – Low Zone 2)
THURSDAY – UNILATERAL (20m EMOM): Step-Ups 10/leg 20 lbs · KB Row 10/arm 25 lbs · DB Curl to Press 10 reps 15 lbs · Russian Twists 20 reps 10 lbs
FRIDAY – REST / MAKE-UP
SATURDAY – WALK: 60 Min Incline Walk (High Zone 2)
