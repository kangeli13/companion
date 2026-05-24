# Companion

A quiet daily check-in for people managing diabetes and high blood pressure. Paste your week's readings, get a plain-language briefing of what's normal, what needs attention, and one small thing to try — plus a clean PDF summary to bring to your next doctor's appointment.

Built for the [DEV.to Gemma 4 Challenge](https://dev.to/challenges/google-gemma-2026-05-06), May 2026.

## Why this exists

There are 537 million people living with diabetes worldwide. Most of them see their doctor once every three to six months. In between, they collect numbers in a notebook or an app and have no idea what those numbers mean together.

Companion is the in-between. It reads a week of glucose and blood pressure readings the way a kind nurse would — looks for danger zones, spots patterns, suggests one specific thing to try, and writes a clinical summary the doctor can scan in 30 seconds.

## How it works

It's a single HTML file. You paste your readings, click analyze, and Google's Gemma 4 (the 26B Mixture-of-Experts model) reads them like text and returns structured insights as JSON.

Your readings never go to any server I control. The call goes directly from your browser to OpenRouter's API, which routes to Gemma 4. Your API key stays in your browser's local storage.

## Why Gemma 4 26B MoE

- **MoE efficiency**: only 4B parameters active per token, so it's fast and cheap to run (free tier on OpenRouter)
- **Long context**: easily handles 7 days of readings plus food notes plus medication logs
- **Reasoning quality**: the "advanced reasoning" track of Gemma 4 — actually spots the rice → high-glucose pattern instead of just summarizing numbers
- **Apache 2.0 license**: the architecture is intentionally swappable to a fully local E4B deployment for privacy-strict markets (German healthcare, EU GDPR contexts)

## Run it locally

No build step. No npm. No backend.

1. Clone or download this repo
2. Open `index.html` in a browser
3. Paste an OpenRouter API key ([get one free](https://openrouter.ai))
4. Click "Load a sample week" to see it work
5. Paste your own readings when ready

## Deploy in two minutes

1. Push this folder to a GitHub repo
2. Go to [vercel.com](https://vercel.com), import the repo, deploy
3. Done — share the URL

## Privacy

- All readings stay in your browser
- The only network call is direct: browser → OpenRouter → Gemma 4 → browser
- API key is stored in `localStorage`, never sent anywhere except OpenRouter
- No analytics, no tracking, no accounts

## Not medical advice

Companion helps you see patterns in your own data and prepare for conversations with your doctor. It is not a substitute for medical care. If a reading is in the danger zone, contact your doctor or emergency services.

## License

MIT
