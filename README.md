# Far Field

A single-page, offline-capable festival guide for mobile phones. Eight festivals
worth planning a year around — three close to home, five worth crossing an ocean
for — what each one is actually like, and how to get there.

- **Live app:** https://pyaeger.github.io/keons-playlist/
- Two files: the app and a service worker. No accounts, no analytics, no backend.
- Works offline after the first online load. Saved progress stays in the browser on the device.
- Install on iPhone: open the link in Safari → Share → **Add to Home Screen** → open once while online.

## What's in it

Eight festivals across the US and abroad, each with dates, ticket guidance,
travel notes and a "Real Talk" section of green and red flags. A match quiz
scores all eight against how you like to travel. A packing kit, a hidden
after-hours tab, and six copy-paste prompts that turn any LLM into an adaptive
interviewer for thinking through what you actually want out of a trip.

An original track, *Twenty-Nine Fine*, plays offline from the app.

## Verification

**[far-field-verification.md](far-field-verification.md)** is
the evidence file for this app, kept deliberately separate so the app stays
clean and the record stays auditable.

Every claim the app makes is listed there with a verified result, a confidence
grade (**H** / **M** / **L**) and a source. It separates organiser-confirmed
festival dates from projected ones, records corrections to earlier drafts —
including two festivals whose schedules the first version got wrong — and
states plainly which content is synthesised from public coverage rather than
first-hand.

It also records what is *not* true: the app cannot sync between devices, live
links need a connection, and saved progress can be cleared by iOS under storage
pressure.

## Known limitation

The app loads its typefaces from Google Fonts, which is the one third-party
request it makes on page load. Self-hosting them would remove it.

## Files

- `index.html` — the entire app (markup, styles, content, logic)
- `sw.js` — service worker for offline caching
- `twenty-nine-fine.mp3` — original track, playable offline
- `far-field-verification.md` — the evidence file
- `guia.html` — redirect stub for the guide that moved to [`mi-guia`](https://github.com/pyaeger/mi-guia)

## Credits

Built by Patrick Yaeger. Music generated with Suno.
