# Far Field

A single-page, offline-capable festival guide for mobile phones. Eight festivals
worth planning a year around — three close to home, five worth crossing an ocean
for — what each one is actually like, and how to get there.

- **Live app:** https://pyaeger.github.io/far-field/
- Two files: the app and a service worker. No accounts, no analytics, no backend.
- Works offline after the first online load. Saved progress stays in the browser on the device.
- Install on iPhone: open the link in Safari → Share → **Add to Home Screen** → open once while online.

## What's in it

Four sections.

**Festivals** — eight of them, three in the US and five abroad. Each carries a
"Real Talk" section of green *and* red flags, dates for the next five years
individually marked Confirmed or Projected, a countdown that knows the
difference, rough cost with a dated caveat, and links out to tickets, lineup,
flights and maps.

**The Afters** — the after-hours and LGBTQ+ scene around each festival city,
with safe-connecting notes.

**Inner Journeys** — six copy-paste prompts that turn any LLM into a patient
interviewer: one question at a time, waiting for your answer before the next.

A festival promises an outer journey: extraordinary music, visuals, dancing, and
the thrill of new friendships. These are the same trip pointed inward —
affirming guides for the curious into identity, creativity, and meaning.

Far Field never sees your answers; the conversation happens wherever you paste
the prompt.

**Guide** — how the app works, and what it does not know.

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
- `LICENSE` — MIT
- `guia.html` — redirect stub for the guide that moved to [`mi-guia`](https://github.com/pyaeger/mi-guia)

## Credits

Built by Patrick Yaeger. Music generated with Suno.

## License

**MIT**, covering everything here — `index.html`, `sw.js`, `guia.html`, the
README, the verification file, and the track *Twenty-Nine Fine*.

The track was generated with Suno under a Pro subscription, and Suno's terms
give Pro subscribers ownership of what they make, so it is licensed on the same
terms as the code. See [LICENSE](LICENSE).
