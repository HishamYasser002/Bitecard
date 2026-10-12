# Bitecard

A mobile-friendly calorie tracker that makes logging food a little more fun. Snap a photo of your meal, get an AI calorie estimate, and unlock a silly collectible card each day you log.

> **Prototype.** I built Bitecard as a Claude artifact. The AI features (calorie estimates from photos, the coach and AI-generated cards) use Claude's built-in artifact runtime, so they only work when the app runs inside claude.ai. Opened anywhere else, it still works as a manual calorie logger that saves to your browser.

## Features

- **Daily calorie target** with a minimum of 1,200 kcal, because very low targets tend to backfire
- **Food logging** with an optional photo, name and calories
- **AI calorie estimate** from a photo or a short description, with a likely range and a per-item breakdown *(claude.ai only)*
- **Progress meter** that turns yellow near the limit and red when you go over, with supportive rather than shaming messages
- **Coach** that suggests what to eat next within the remaining budget *(claude.ai only)*
- **Daily mystery card**: log 2 items to unlock an animated collectible card (common, rare or legendary)
- **7-day history** chart with streaks and days within target
- Light and dark mode, and reduced-motion support

## Run it

It's a single HTML file with no build step. Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
```

Then go to `http://localhost:8000`. Outside claude.ai, data is stored in your browser's `localStorage`.

## How it's built

- One self-contained `index.html`: HTML, CSS and vanilla JavaScript, no framework
- Inside claude.ai it uses the artifact runtime for AI calls, per-user storage and identity, and falls back to `localStorage` when that runtime isn't available
- Card animations are pure CSS: dancing, orbiting, parading, rocket launches, falling emoji and a foil shine on legendary cards

## Roadmap

Rebuilding it as a standalone app on Azure, so the AI features work anywhere:

- [ ] Azure Function as the backend for AI calorie estimates
- [ ] Table Storage or Cosmos DB for user data
- [ ] User accounts
- [ ] CI/CD with GitHub Actions
