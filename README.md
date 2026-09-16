# Fuel Ledger

A calorie and macro tracker you drive with plain English. Describe a meal
("2 eggs, 3 strips of bacon, a slice of sourdough with butter"), and the page
breaks it into items and estimates calories, protein, carbs and fat. Log your
training and the day's targets move with it.

Published as a Claude Artifact: https://claude.ai/artifact/FE9H7HHTLi6bYp1TyDfJfC

## What it does

- **Photo and label scanning.** Point the camera at a nutrition facts panel and
  it reads the serving size and per-serving numbers, multiplied by however many
  servings you ate; point it at a plate and it names the foods and estimates the
  portions from what's visible. Results land in the same editable review list as
  a typed description. Shown only where the view can send images to Claude.
- **Meal estimates from a description.** Claude looks the food up when the page
  can reach it; otherwise a built-in table of ~180 foods with portion parsing
  (grams, ounces, cups, slices, strips, "a large bowl of…") does the job
  offline. Every estimated line is editable before it goes in the log.
- **Phases, not one fixed goal.** Cut / Recomp / Maintain / Lean bulk, each
  carrying its own deficit and macro split (protein stays at 1.0 g/lb through a
  cut and a recomp — that, plus heavy training, is what holds muscle while fat
  comes off). Set a goal weight and the page tracks progress, projects a finish
  date from both your planned pace and the pace the scale is actually moving,
  and offers you the next phase once your trend weight arrives. Switching phase
  rebuilds every target around the new goal and restarts progress tracking.
- **Targets from your own numbers.** Mifflin–St Jeor BMR from age, sex, height
  and weight, times a daily-life activity multiplier that deliberately excludes
  workouts, minus (or plus) 500 kcal per pound per week of goal rate, with a
  safety floor.
- **Macros.** Protein set per pound of bodyweight, fat as a share of calories
  with a 0.28 g/lb floor, carbs take the remainder. Cutting faster than 1% of
  bodyweight a week gets flagged, and when calories run short before protein
  does, the day's summary says to spend what's left on protein.
- **Training raises the budget.** MET values from the Compendium of Physical
  Activities, net of resting metabolism so nothing is double-counted, with an
  eat-back setting of none / half / all. Steps count too.
- **Trends.** 14-day intake against target, daily macro composition, and a
  weigh-in chart with a 7-day moving average plus the weekly rate it implies.
- Quick-add favourites, per-day navigation, CSV export.

The log starts empty — no seeded sample data. If anything throws, the message
is kept under Setup -> Data rather than disappearing.

## Layout

`app.html` is the artifact source, exactly as published. Artifacts supply the
`<!doctype>`, `<head>` and `<body>` wrapper at publish time, so the file starts
at `<title>`; browsers open it fine as-is. Everything is inline — no build step,
no dependencies beyond Google Fonts.

Storage: the artifact's private document store when available (so the log
follows you between devices), with `localStorage` as the fallback and cache.
