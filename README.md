# Fuel Log — install on your phone

A self-contained app. No build step, no framework, no server code. Four files.

## What you've got

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `manifest.json` | Makes it installable |
| `sw.js` | Offline support |
| `icon-192.png` / `icon-512.png` | Home screen icon |


## Features

**Diary** — meals split into Breakfast / Lunch / Dinner / Snacks, auto-picked by time of day. Log by typing, by photo (camera or gallery), by Quick add (kcal + protein only), from a Saved meal, or manually. AI estimates come back fully editable before saving.

**Saved meals** — tap the star beside any meal to save the whole thing. One tap to re-log it another day.

**Water** — quick +250/500/750ml buttons on Home, tracked against a daily goal.

**Supps** — name, dose, timing and optional macros per serving. Anything with macros (whey, mass gainer, meal shakes) feeds straight into that day's food diary when you tick it, and comes back out if you untick. Creatine and vitamins carry no macros, so they just tick. Photo the labels and the AI reads names and strengths. Seven-day grid per supplement.

**Meds** — countdown to next dose. Turn on reminders for a real notification when one falls due.

**Body** — weight with goal and projected date based on your actual rate, smart-scale metrics (body fat, muscle, water, BMI, visceral, bone, BMR), daily activity from fitness-app screenshots, golf rounds with scoring averages, and gym sessions.

**Gym** — its own tab. Push / Pull / Legs pre-loaded, with a week strip showing what you've trained. Every exercise has coaching notes: how to set up, how to execute, the cue that matters and the common mistake to avoid. Tap ⓘ beside any exercise, in the routine list or mid-set. Full exercise guide with search.

**Workouts** — Push / Pull / Legs pre-loaded. Start a session, log weight and reps per set, and see last session's numbers plus your best set beside every exercise. Tracks duration, set count and total volume. Add exercises mid-session or run a freestyle session. Full history with every set.

**Train** — start a Push/Pull/Legs session or a freestyle one, log every set with weight and reps, see last session and personal best per exercise, and tap the info icon beside any exercise for form cues.

**Two PDF reports** — a training & nutrition overview for a coach (macro wheel, colour charts, body composition, every session and set, exercise progression, activity, golf), and a meal diary showing each day broken out by meal with its own macros, daily macro wheel and optional meal photos. Both print straight to PDF.

**Old trainer report** — a printable PDF covering the selected period: nutrition averages against targets, adherence, body composition, every session and set, exercise-by-exercise load progression, golf and supplements. Tap the button, choose Save as PDF, send it to your coach.

**Stats** — 7/30/90-day averages, consistency breakdown, calories by day of week, streaks, and CSV export.


## Data notes

**Photos** are stored in IndexedDB, not localStorage, because images are far too big for it. They are kept on the device only and are **not** included in the JSON backup under the backup icon — if you move devices, your log comes across but the pictures don't.

**Nutrition fields** follow Irish/UK label conventions: energy, protein, carbohydrate, of which sugars, fat, of which saturates, fibre, and salt (grams of salt, not sodium).

## Getting it on your phone (10 minutes, free)

It needs to be served over **https** to install properly. Easiest route is GitHub Pages:

1. Go to **github.com** → **New repository** → name it `fuel-log` → set to **Public** → Create.
2. Click **uploading an existing file** and drag in all five files (not the folder — the files themselves).
3. Commit.
4. Repo **Settings** → **Pages** → under Source pick **Deploy from a branch**, branch `main`, folder `/ (root)` → Save.
5. Wait ~1 minute. Your app is at `https://YOURNAME.github.io/fuel-log/`

### Install it

Open that URL in **Chrome on your phone** → menu (⋮) → **Add to Home screen** / **Install app**.

You'll get a proper icon, it opens fullscreen with no browser bars, and it works with no signal.

Alternative to GitHub Pages: **Netlify Drop** (app.netlify.com/drop) — drag the folder onto the page, get a URL instantly, no account needed to start.

## Your data

Stored in `localStorage` on the device. It stays there — closing the app, rebooting, going offline, none of it matters.

**It does not sync between devices.** Use ⇅ → Download file to move a backup across, or just keep one device as the source of truth.

Back up occasionally: ⇅ → **Download file**. Restore with ⇅ → **Load file**.

## AI macro parsing (optional)

Typing meals in plain English and photo analysis both need an Anthropic API key.

1. Get one at **console.anthropic.com** → API keys.
2. In the app: ⇅ → paste into the AI KEY box → Save key.

The key lives only in your phone's storage — it is never in the code and never leaves your device except to call the API directly.

**Keep the repo public but never paste your key into a file you upload.** Enter it in the app on your phone only.

Cost is pennies — each meal parse is a fraction of a cent. Without a key the app works fine, you just enter macros manually.

## Changing things

`index.html` is plain HTML/CSS/JS. Themes are the `THEMES` object at the top of the script. Edit, re-upload the file to GitHub, changes go live in a minute.
