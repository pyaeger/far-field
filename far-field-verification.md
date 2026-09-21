Far Field — Claims Verification & Deployment Notes
Prepared June 2026. This document is the evidence file for the app. It is intentionally kept separate from the app itself so the app stays clean and this stays auditable. Confidence labels: H = high, M = medium, L = low (L/M explained).
1. Device compatibility
Claim
Verified result
Confidence
Source
iPhone 8 runs the app
Yes. iPhone 8 caps at iOS 16.7.x and cannot install iOS 17+. The app targets iOS 16, so it runs.
H
Apple Support community; Macworld iOS support guide
iPhone 8 can "update to iOS 17 soon"
No — this is not possible. The iPhone 8 (A11 chip) is permanently limited to iOS 16. iOS 17 requires A12 (iPhone XS or newer). The 8 stays on 16.
H
Apple Support community; Wikipedia iOS 17 supported-devices
iPhone 13 runs the app
Yes, and better. The 13 runs iOS 17 and well beyond (current iOS line).
H
Apple support lists
iOS 16 still gets security patches
Yes, as of May 2026 Apple was still issuing iOS 16 security updates for the iPhone 8/X generation, though this is not expected to continue much past September 2026.
M
Macworld (3 days old at time of writing)
Implication: the two-phone split is real and permanent — the 8 is iOS 16 forever, the 13 is the modern one. The newer device should be kept updated; the 8 still works but is increasingly out of long-term support.
2. App capability claims
Claim
Verified result
Confidence
Notes
"Add to Home Screen" gives an app-like, full-screen launch on iOS 16/17
True. Supported well before iOS 16. Install is manual (Share → Add to Home Screen); iOS shows no automatic install prompt.
H
Standard iOS behaviour; multiple PWA references
Works offline
Only true with a service worker — which the app now includes (sw.js). Without it, a home-screen page shows "No internet connection" when offline. Offline works after the first online load caches the page.
H
Apple Developer Forums thread documents the no-service-worker failure; this is why sw.js was added
Saved data (checklist ticks, unlocked Afters tab) persists
True via localStorage. iOS can clear site data under storage pressure or long disuse; home-screen apps are more protected than plain Safari tabs, but persistence is not guaranteed. Safari 17 added a Persistent Storage API and larger quotas.
M
PWA-on-iOS 2026 references. M because eviction behaviour varies by iOS version and usage.
Visuals (gradients, blur glow, slide-up sheet, fl/grid layout) render on iOS 16
True. All are long-supported in iOS 16 Safari (WebKit).
H
—
Countdown, quiz, filters, secret unlock
True. Plain JavaScript, nothing version-sensitive.
H
—
Smooth on the older iPhone 8
Expected yes. The animated glow is the only demanding element; the app now auto-disables the glow animation if it measures a low frame rate on load, and respects reduced-motion.
M
M because performance is device-state dependent; the safeguard is insurance, not a guarantee.
No accounts by design. Because there is no server, each phone stores its own progress. The checklist and the unlocked Afters tab do not sync between the iPhone 8 and the iPhone 13. (H)
3. Festival dates — confirmed vs projected
Only organiser-announced dates are labelled Confirmed. Future years marked Projected use each festival's long-standing scheduling pattern and are not official.
Festival
2026
2027
2028
2029
2030
Confidence on confirmed rows
Tomorrowland (Boom)
Jul 17–19 & 24–26 ✅
Jul 16–18 & 23–25 ✅
late July (proj)
late July (proj)
late July (proj)
H
Glastonbury (Worthy Farm)
None — fallow year ⛔
Jun 23–27 ✅
late June (proj)
late June (proj)
late June (proj)
H
Fuji Rock (Naeba)
Jul 24–26 ✅
late July (proj)
late July (proj)
late July (proj)
late July (proj)
H
Sziget (Budapest)
Aug 11–15 ✅
mid-August (proj)
mid-August (proj)
mid-August (proj)
mid-August (proj)
H
Rock in Rio (Rio)
Sep 4–7 & 11–13 ✅
None (biennial) ⛔
September (proj)
None (biennial) ⛔
September (proj)
H
Key corrections from the first draft:
Glastonbury has no 2026 festival — it is a planned fallow year; the next is 23–27 June 2027. (H — Glastonbury official + BBC + Time Out)
Rock in Rio (Rio) is biennial, running in even years; there is no Rio edition in 2027 or 2029. (H — confirmed 2026 dates; biennial pattern from edition history)
Tomorrowland 2027 is already public (Jul 16–18 & 23–25). (H — multiple outlets / countdown pages)
Ticket-status notes (true as of June 2026, will change):
Tomorrowland 2026 passes are largely sold out — resale only, or target 2027. (M — volatile)
Fuji Rock 2026 3-day and Saturday GA sold out; Friday/Sunday and Friday-night tickets remained. (M — volatile)
Rock in Rio 2026 pre-sale broke records; buy early via Ticketmaster Brasil. (M — volatile)
Sources for dates: organiser sites (Glastonbury, Tomorrowland, Sziget, Fuji Rock, Rock in Rio / Visit Rio), plus BBC, Time Out, DJ Mag, Songkick, Tokyo Cheapo, Omelete.
4. "Real Talk" sourcing
The green/red flags and tips are synthesised from public attendee coverage and festival guides, not lived experience. The app states this plainly on every festival card ("Gathered from real festival-goers, not first-hand"). (H — this is a transparency statement, not a factual claim about the world.)
5. Deployment notes
The app is now two files — this is the cost of genuine offline on iOS:
index.html — the app
sw.js — the service worker (must sit next to the HTML, same folder, same domain)
To publish (no server to run):
Upload both files to free static hosting — Cloudflare Pages or GitHub Pages (drag-and-drop). The HTML can be named index.html so the URL is clean.
Hosting must be HTTPS (Cloudflare/GitHub Pages are by default). Service workers and Add-to-Home-Screen require it. (H)
Open the link on the target device: Safari → Share → Add to Home Screen.
Open it once while online so the service worker caches it; after that it works offline, which matters on a WiFi-only device. (H)
Known limitations (all by design / platform):
No cross-device sync (no accounts / no server). (H)
Live links (tickets, Spotify, maps, flights) need a connection; only the curated content works offline. (H)
Saved progress can be cleared by iOS under storage pressure. (M)
Projected future dates are estimates — always reconfirm on the official site. (H)
6. Version 2 — featured picks (added)
Three US festivals were added and pinned at the top of the home screen as "Featured" with a star badge. The original five remain below as the "Bucket list" group. The app now holds 8 festivals.
Festival
Location
2026 (confirmed)
2027–2030
Confidence
Source
Electric Forest
Double JJ Resort, Rothbury, MI
Jun 25–28 ✅
late June (projected)
H
Electric Forest official IG; Wikipedia; EDM Identity
Lollapalooza
Grant Park, Chicago, IL
Jul 30 – Aug 2 ✅
late July / early Aug (projected)
H
lollapalooza.com; ABC7 Chicago; Choose Chicago
EDC Orlando
Tinker Field, Orlando, FL
Nov 6–8 ✅
early November (projected)
H
EDC Orlando official; Ticketmaster; EDM Identity
Festival facts verified:
Electric Forest: all ages; camping; electronic + jam-band mix; ~40,000–50,000 attendance; nearest airport Grand Rapids (GRR). (H)
Lollapalooza: 4-day, ~170+ artists across 8 stages; all ages; non-camping (downtown Grant Park); 4-day passes were on a waitlist as of 2026. (H; ticket status M — volatile)
EDC Orlando: 18+ general admission, 21+ VIP — government photo ID required; non-camping; ~25 min from MCO airport; gates 1pm. (H)
Projected rows for these three use each festival's established annual window (late June / late July–early Aug / early November) and are not organiser-confirmed past 2026. (H that they are estimates.)
Other v2 changes:
The match quiz now scores all 8 festivals, and the travel question changed to "Stay in the US / Cross an ocean" to fit the mixed list. (H)
The Afters tab gained entries for all three picks (Forest Family; Chicago / Northalsted; Orlando). (H)
Service worker cache bumped to v3 — installed phones will pull the new version on their next online open. Re-upload both files to the same GitHub folder. (H)
Deployment is 2 files (index.html + sw.js). (H)
7. Version 3 — in-app Guide + Inner Journeys
Guide moved into the app. It's now a styled in-app page (matching the dark/neon look), reached from a menu icon in the top-right header, opening with a build credit. (H)
New "Inner Journeys" page (same header menu): six copy-paste prompts that turn any LLM into an adaptive interviewer. Each prompt instructs the AI to ask one question at a time, wait for the answer, confirm readiness before continuing, and adapt the next question to the prior response; it ends with a synthesis. Themes: Personality & Inner Wiring; Experiences You Crave; Identity & Authenticity; Connection & Belonging; Music & Joy; Growth & The Next Chapter. Each has an optional "[your specific angle]" slot. (H)
Copy buttons use the Clipboard API with a hidden-textarea fallback for older iOS Safari. (M — clipboard behaviour varies by iOS version; fallback covers the gap.)
Navigation: bottom bar unchanged (Festivals · Match · Kit · Afters-when-unlocked); Guide and Inner Journeys live in the header menu to avoid overcrowding the bar. (H)
Service worker bumped to v5. Re-upload both files to GitHub; phones refresh on next online open. (H)
The Afters access (for reference): triple-tap the "Far Field" title on the home screen. Now also documented inside the in-app Guide. (H)
8. Live ticket prices verified (June 2026)
Face-value/official figures where available; resale marketplaces run higher and are excluded. All remain approximate and the app links out to confirm.
Festival
Price (approx, face)
Source
Electric Forest
~$450+ 4-day GA + camping
AXS / official history
Lollapalooza
~$400+ 4-day GA; single-day ~$150
lollapalooza.com / Time Out
EDC Orlando
$220 GA / $300 GA+ / $420 VIP (3-day, early-bird)
EDM Identity / Front Gate
Tomorrowland
€400 Full Madness; Day Pass €153
official 2026 pricing / festivalviewer
Glastonbury
£373.50 + £5 (2025); 2027 TBC
Glastonbury official
Fuji Rock
¥59,000 3-day; ¥26,000 1-day
Japan Web Magazine / official
Sziget
~€350+ 5-day pass; day tickets less
szigetfestival.com
Rock in Rio
R$870 GA day / R$435 half
official / Visit Rio
Prices are volatile and tier-based; treat as ballpark and confirm on the official site before buying. (Confidence: H that these were the figures as of June 2026; M that they hold, since tiers rise and sell out.)
Service worker bumped to v6.
9. Personal song added (v7)
A native HTML5 <audio> player card "Twenty-Nine Fine" added to the top of the home dashboard (play/pause/scrub, works on iOS + Android). Audio is not autoplayed (iOS blocks it) — tap to play. (H)
The player references ./twenty-nine-fine.mp3 in the same folder as index.html. Upload the provided twenty-nine-fine.mp3 to the GitHub repo root alongside index.html and sw.js. It runtime-caches for offline after the first online play. (H)
Service worker bumped to v7.

---

## Provenance note — September 2026

This app began as a personalised birthday gift and has been repurposed as a
general festival guide. The recipient's name, photograph, age, the dedication
and the event location were removed from the app, the service worker and this
document; the embedded JPEG (~25 KB) was deleted from `index.html`.

The song, the app, the design and this verification record are the author's
own work. The track was generated with Suno by Patrick Yaeger.

Earlier commits in this repository still contain the removed photograph and
name. Removing them there requires rewriting history.

---

## Version 4 — renamed *Far Field*, one navigation bar (September 2026)

**Name.** The app is now **Far Field**. Changed in the `<title>`, the
`apple-mobile-web-app-title`, the meta description, the splash screen, the
header wordmark, the in-app Guide, the service worker and this document's
title. The Afters easter egg is now a triple-tap on the "Far Field" wordmark.
The repository was renamed `keons-playlist` → `far-field` on 2026-09-21, and the
live app moved with it to `https://pyaeger.github.io/far-field/`. GitHub keeps a
permanent redirect from the old name, verified by request: the old URL returns a
301 to the new one, so existing links and any installed home-screen copy keep
working. That redirect dies the moment a new repository is created under the old
name, so the name should stay unused. (A — HTTP response)

**Composition, stated plainly.** Eight festivals: **three in the US** —
Electric Forest (Michigan), Lollapalooza (Chicago), EDC Orlando — which are
also the three Featured picks, and **five abroad** — Tomorrowland, Glastonbury,
Fuji Rock, Sziget, Rock in Rio. Earlier copy described the app as being about
"crossing an ocean," which describes only the five. (H — counted from the
`FESTS` array.)

**Navigation.** The header menu is gone. Guide and Inner Journeys moved into
the bottom bar, which now carries Festivals · Match · Kit · Journeys · Guide,
plus Afters once unlocked. Measured at 320, 360 and 390 px viewport widths
with all six buttons shown: no overflow, no horizontal page scroll. (H —
measured in headless Chromium.)

**Getting out of a festival page.** Three ways now, where there was one:
- the bottom bar stays visible over an open festival page (its `z-index`
  dropped below the bar's, and its bottom padding clears it);
- the back control is labelled **← Festivals** rather than a bare arrow;
- opening a festival pushes a history entry, so the phone's Back gesture and
  the Escape key close the page instead of leaving the app. (H — all three
  verified in headless Chromium, including `history.back()`.)

**Gutter.** The page gutter went from 16 px to 20 px, and a soft radial glow
sits behind the wordmark. The wordmark is gradient-filled text with no
background of its own, so at 16 px its ink sat on the gutter line while
adjacent cards' content began further in. (H)

**Service worker bumped to v10** (`far-field-v10`). Installed phones pull the
new version on their next online open. (H)

### Dates now derive from the editions table

Previously each festival carried a hard-coded `cd` countdown timestamp and a
hard-coded `next` display string, independent of the Dates table below them.
By 2026-09-20 six of the eight `cd` values had already passed — Electric Forest
(2026-06-25), Tomorrowland (2026-07-17), Fuji Rock (2026-07-24), Lollapalooza
(2026-07-30), Sziget (2026-08-11) and Rock in Rio (2026-09-04) — so those six
showed the fallback line *"Check the official site for the next confirmed date"*
instead of a countdown. Only EDC Orlando and Glastonbury still counted down. (H)

Both fields are gone. Each edition row is now
`[year, text, grade, start, end]`, and the next edition, the countdown target
and every "Next:" label are computed from it. There is one source of dates in
the app, and it is the same table the user reads. (H)

**Projected dates are anchored on the confirmed edition's month and day.**
Electric Forest's 2027–2030 rows count down to 25 June of each year because the
confirmed 2026 edition ran 25–28 June. These are *derived*, not sourced: the
row text still reads "Late June (projected)", the card label reads
"Jun 2027 (est.)", and the countdown reads *"to the festival's usual 2027
window — projected, not yet announced. Confirm before booking anything."*
A projected countdown is a guess with a clock on it and is labelled as one. (Derived)

**Fallow and biennial years are skipped, not counted.** A plain "same window,
next year" rule would be wrong for two of the eight: Glastonbury takes fallow
years and Rock in Rio's Rio edition is biennial. Both already had `n` rows in
the table, and the next-edition search skips them. Verified by simulation: on
2026-09-21 Rock in Rio resolves to **2028**, not 2027. (H)

**An edition stays "next" until the day after it ends**, so a festival reads
*"Happening now"* while it runs rather than flipping to next year on opening
day. Verified at a simulated 2026-06-26: Electric Forest resolves to the live
2026 edition. (H)

#### Verified by simulation

Next-edition resolution was checked for all eight festivals at six simulated
dates — 2026-09-21, 2026-06-26, 2026-11-07, 2027-07-01, 2028-01-01 and
2031-01-01 — in headless Chromium, with no page errors. Results on
2026-09-21: EDC Orlando Nov 2026 (confirmed), Tomorrowland Jul 2027
(confirmed), Glastonbury Jun 2027 (confirmed), the other five projected,
Rock in Rio correctly at 2028. (H)

#### The remaining cliff

The editions tables end at 2030. From 1 January 2031 every festival resolves
to no edition and shows *"No further editions listed here — check the official
site."* The app degrades to an honest message rather than a wrong date, but it
does stop being useful on that date unless the tables are extended. (H)

#### Still stale

The ticket figures in section 8 were verified in June 2026 and are three months
old. Nothing in this release re-verified them; they remain M — volatile.

---

## Version 5 — header alignment and a usable genre filter (September 2026)

### Left alignment

Reported: the title and tagline sat against the left edge with no visual
padding. Version 4 had moved the page gutter from 16 px to 20 px and confirmed
the number changed — which fixed nothing, because the gutter was never the
problem. Measured at 390 px, the wordmark, tagline and card *edges* all sat at
20 px while the card *text* sat at 37 px. The eye compares text to text, so the
largest type on the page read as flush against the edge. (H — measured)

The wordmark, tagline and chip row now carry a 16 px left margin, placing them
at 36 px, the same column as the card copy. Card borders stay at 20 px: boxes
on one line, text on another. (H)

### The chip row on a desktop

The row is `overflow-x: auto` with both `scrollbar-width: none` and
`::-webkit-scrollbar { display: none }`. On a phone the finger is the
affordance. On a pointer device there was **no affordance at all**: a plain
mouse wheel scrolls the page, not the row, and nothing indicated the row
continued. Because `.app` is capped at `max-width: 560px`, a desktop visitor
saw about 6 of 14 chips with 625 px unreachable. Shift+wheel, a trackpad swipe
and the Tab key all worked — the chips are real `<button>` elements — but none
is discoverable. (H — measured at 1440 px)

Fixed on two axes: `@media (hover:hover) and (pointer:fine)` wraps the row so
every filter is visible without a gesture; `@media (hover:none),(pointer:coarse)`
adds a right-edge mask so touch users can see the row continues. (H)

### The genre list was cut from 13 to 5

Counted across the 8 festivals, **seven of thirteen genres matched exactly one
festival**: Arts, Carnival energy, Eclectic, Hip-Hop, Indie, Jam Band, Outdoors.
With 8 items in the list, a filter narrowing to 1 returns less than scrolling
already showed. The row also mixed two axes — musical genre (EDM, Electronic,
Rock, Pop, Hip-Hop, Indie, Jam Band) against vibe and format (Everything,
Mainstage, Arts, Outdoors, Carnival energy, Eclectic) — presented identically,
so the row had no logic to learn. (H — counted from the `FESTS` array)

Remaining filters, ordered broadest first:

| Filter | Festivals |
|---|---|
| All | 8 |
| Electronic | 5 |
| EDM | 3 |
| Multi-genre | 3 |
| Pop | 3 |
| Rock | 3 |

`Everything` was renamed `Multi-genre`: tapping it returns three festivals, not
everything, and what it actually means is that those three span genres rather
than specialising. (H)

**This change is subtractive and renaming only. No genre was added to any
festival.** Tagging Rock in Rio "Hip-Hop" would tidy the filter and would also
be an unsourced claim about that festival's programming. The dropped traits are
not lost — Electric Forest's jam-band character and Fuji Rock's outdoor setting
are already stated in their Real Talk sections, which is where detail belongs
rather than a filter bar. (H)

Verified by clicking every chip and counting results: the six counts above,
no page errors. Desktop 1440 px: one row, nothing hidden. Phone 390 px: 104 px
still scrolls behind the fade; 320 px: 174 px. (H)

No service-worker bump — the worker is network-first for navigation, so an
updated `index.html` lands on the next online load. `far-field-v10` stands.
