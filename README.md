# UMF Miami 2026 — Set Times Tracker

A mobile-first, installable web app for navigating Ultra Music Festival 2026: browse the full lineup across every stage and day, favorite the artists you want to see, get **clash warnings** when your picks overlap, and receive **browser notifications** before a set starts.

**Live:** _add your deployed URL here (e.g. Netlify / GitHub Pages)_

---

## Features

- **Full festival schedule** — 166 sets across **3 days** and **7 stages** (Main, Worldwide, Megastructure, Hekate/M2, Live, UMF Radio, Oasis), each color-coded by stage.
- **Favorites** — tap to save the artists you care about; your picks persist across sessions via `localStorage`.
- **Set-clash detection** — automatically flags when two of your favorited sets overlap in time, so you can plan your route through the festival.
- **Set reminders** — opt-in **browser push notifications** fire a configurable number of minutes before a favorited set begins.
- **Timeline / gantt view** — a scrollable time-ruler visualization of the day with a live "now" indicator and countdowns to upcoming sets.
- **Day & stage filtering** — quickly switch between days and jump to a specific stage.
- **Installable PWA** — add-to-home-screen support on iOS/Android with a web app manifest, apple-touch-icon, and themed status bar for a native-app feel.
- **Polished dark UI** — neon festival aesthetic, responsive and touch-friendly.

## Tech Stack

- **Vanilla JavaScript** — no frameworks; hand-rolled state, rendering, and event handling
- **Web APIs** — `localStorage` (favorites), the Notifications API (set reminders), and a PWA **web app manifest** (installability)
- **HTML + CSS** — single-file app, CSS custom properties for theming, mobile-first responsive layout

## How It Works

```
Set database (166 sets: artist, stage, day, time)
        │
        ▼
 Render schedule ──► user favorites sets ──► saved to localStorage
        │                                          │
        ▼                                          ▼
 Clash detection over favorites          Notification scheduler
 (overlapping times → warning)           (fires ~N mins before set)
```

## Project Structure

```
.
└── index.html   # Complete self-contained app: data, UI, styles, and logic
```

Everything — the set data, styling, and all interactivity — lives in a single `index.html`, so it deploys anywhere static with zero build step.

## Running Locally

```bash
# open directly, or serve the folder:
python3 -m http.server 8000
# then visit http://localhost:8000
```

> Notifications require granting permission in the browser and a page that stays open; on iOS, notifications work best when the app is installed to the home screen.

## Notes

Built as a personal project to solve a real festival-planning problem: with seven stages running in parallel, figuring out where to be and when is genuinely hard. The clash-detection and reminder features turn a static lineup into an actual planning tool. Demonstrates state management, the Notifications and Web Storage APIs, PWA fundamentals, and data-driven UI rendering — all in dependency-free vanilla JS.
