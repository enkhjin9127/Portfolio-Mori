# Portfolio site

Static site. No build step, no package dependencies, no framework — plain HTML,
two stylesheets, four scripts, inline scripts on two pages, and GSAP from
cdnjs plus Lenis from jsdelivr on the landing page only. Edit a file and reload.

## Running it

```bash
python3 /Users/mundagroki/Downloads/Work/Portfolio/serve.py
```

Serves on `http://localhost:4173` (a port argument or `PORT` overrides it).
`serve.py` serves its own folder (`ROOT` from `__file__`, since 2026-09-30:
a hardcoded path broke when the folder was renamed from "Portfolio Website").
In the sandbox run it by its absolute path: `os.getcwd()` is blocked there, so
a relative `python3 serve.py` can't resolve itself.

On the Windows laptop (no Python; Node is at `D:\Program Files\node.exe`,
not on PATH) run `serve.mjs`, its Node twin, the same way: same port, AVIF
type and no-cache, serving its own folder. Kept out of the deploy with
`serve.py`.

```bash
"/d/Program Files/node.exe" D:/Portfolio-Mori/serve.mjs
```

`.claude/launch.json` only *attaches* to that URL; it does not start the
server. A managed server does not work here — the preview sandbox cannot read
files under `~/Downloads` (macOS TCC), so the server has to be started by hand.
If every path suddenly 404s, the server has gone stale: kill it and restart.

## Pages

| File | Page |
|---|---|
| `index.html` | landing, one page (2026-09-28/29, owner's asking): the chest-opening hero, then About and My Work under it, on one ground. The categories menu that came up on the black is gone; About rises out of the blackout (`.one`, `margin-top:-48vh`: the blackout is done at 86 of the timeline's 100, and a spacer tween keeps the timeline 100 long so the frame windows keep their place). About began as a copy of `about.html` (without its closing "Open to work" block, taken off on 2026-09-29), scoped to its section; about.html is gone now (2026-09-30), so this is the only one. My Work sits on About's ground: its хана and grain laid on `.one` as backgrounds that scroll with the page (`.one::before`/`::after`; the хана's 14° lean baked into a seamless 346px tile). They are never pinned to the screen here: pinned, as on about.html, across this length they made the owner feel sick (2026-09-29). The grain lies under the words at .1 (about.html lays it over them at .13, which specked every letter and made the text hard to read): My Work opens on a transition after trionn.com's (`.tz`, owner's asking 2026-09-29, "copy this transition, change the colours"), measured off theirs in headless Chrome: one screen pinned and five full-width stripes that each grow up from their own foot, the lowest first (theirs: each starts .214 of a screen after the one under it and fills in .858, so the screen is covered at 1.72 and holds; theirs also has a huge marquee drifting left, which ours no longer has). Ours are `STEP` .32 and `LEN` 1.4, so they close in 2.68 screens of scroll (since 2026-11-14, owner: "transition is too fast", once the wheel went from .8 to 1.5: at .17 and .75 they closed in 1.4 screens, 1.75 of wheel input at .8, and this is 1.79 of input at 1.5, the same feel; measured at 1440×900, they rise from 1.6 to 4.28 screens from the pin and it lets go as the last closes. Before that: .12 and .52, one screen, after "still so much space"; slowed to .17/.75 on 2026-09-29 when the owner found the transition "comes in too fast"), and the pin lets go the moment they close (`RUN` = 4×STEP + LEN), since a held covered screen read as empty clouds (owner: "reduce the space"). Our stripes carry the timeline's own ground (black, the gold clouds anchored at the screen's foot, the grain), so the covered screen is already the timeline and it scrolls on without a seam. Behind the words, the pinned screen carries the page's own хана and grain (`.tz-bg`, owner's asking 2026-09-29: "keep түмэн өлзий хээ on that section"), their tiles set where the page's lie when it arrives (`--tz-hx`, `--tz-y`; no seam at full resolution); pinned, it holds still with the screen and the stripes rise over it. **The bichig sentence, its drum and its hearth are off the landing since 2026-11-21** (owner: "remove drums for now"): the transition is the stripes alone, rising from the pin over the хана screen (section 1 + RUN screens tall, no wait), hidden off `.is-on`; the last code with them is commit 3429d32. What follows describes them as they were. Experience's line and marks now match Recent work's (same stroke, lit #e4cf9f with a 140px soft edge, diamonds with the same halo; owner's asking the same day). **Before the stripes, the owner's sentence in Mongol bichig is written in on the scroll** (`.wr`, the owner's pick on 2026-09-29 of three ideas): "ухаан бодол нь ундарга шиг ундарж, уран бүтээл нь уул шиг сүндэрлэг" (given by the owner; don't respell it; the visually hidden `<p class="sr" lang="mn-Mong">` carries it for screen readers). The whole of it is set large in four lines, each clause two (`.wr-l`, the second clause .28em further down), left-aligned in a block centred on the screen, `clamp(30px,min(7vw,10.5vh),128px)` (94.5px at 1440×900; it was 112 until the owner asked for it "a little bit smaller"). A brush writes it in left to right, line after line, as the page scrolls: its edge is soft (`FEATHER` .35em), the ink just behind it is fresh, paler and still wet (`WET` 1.3em, fading from rgb(241,227,191) into the matte gold), and between lines it lifts for `LIFT` .9em of its travel. Scroll back and it unwrites. The words it hasn't reached wait as a faint trace (the text itself at rgba(239,231,218,.08), as on a practice sheet). The ink is a canvas laid exactly over the text (`.wr-ink`): each line is drawn once, whole, into its own bitmap at the font's own baseline (so its letters keep their joined forms), and each frame only reveals them (one line through a scratch canvas: `source-atop` for the wet ink, `destination-in` for the edge), so nothing in the page repaints. **When the writing is done, the four lines roll up into rings and turn** (owner's asking, 2026-09-29: "spin them like previous animation but without any additional elements"): the drum after Nika D.'s "Moving text animation" (dribbble.com/shots/13916052), words only (no ✣, glow or frame), the front in gold and the back seen through mirrored at .3. Each ring is its written line repeated round one shared circumference with plain gaps (`drum()` picks the circumference, a radius between 3.1 and 5.2 of the text's ems and no more than .4 of the screen's width, that gives every line a gap nearest 1.1em; so the drum shrinks with the words), drawn into a texture and dealt across flat panels 34px wide (`PANEL`, a whole number so the joins fall on whole pixels) with two faces each; 316 panels at 1440. Each line coils into its ring as soon as the brush has written it and is half way through its lift to the next, so the drum builds from the top while the lines under it are still being written (owner's asking, 2026-09-29: "when I turn here, the upper line spins into the drum, and lines 2, 3, 4 the same"; "snap into the drum fast"; then "it bends on both sides: I want the first side to bend first and circle, then the letters after follow it, like the snake game"). It plays on its own, in time, not on the scroll, over `UP` 3s (2.2 at first; owner: "spin them a bit slowly"); scrolled back before that point (with a hundredth of the writing's hysteresis, so it doesn't flicker there), it runs back out onto its written line in `DOWN` 1.8s. **The coil is the snake game** (`rollRing()`): the line's first letter is the head; it curls back into a circle that starts small (`RHO0` .3 of the drum's radius) at that letter, and the rest of the line follows exactly along its path, the flat body sliding left after the head and turning into the coil where the head turned, never bending on its own. As it goes the circle grows to the drum's size and glides from the line's head to the middle, on a quick-off-the-mark ease with a long soft landing (1 − (1 − f)³(1 + 3f)). L, how much of the snake has gone into the coil, is the coil's own part (C·ρ·e) plus the turn in time (S, eased in over the first .7), so the moment it closes it is already turning and just goes on round and round like the drum it came from. The snake is the whole ring's length, the line and then its copies with plain gaps; the copies are its tail, unseen while flat (shown, they read as a second line sliding in to the right of the first before it bent) and fading in over .8em as they go round into the coil, all of it up by the end. Closed, S wraps every copy (`off`, which copy the head is on), so rolled back the snake runs back out and lands on the written line. Tried the same day and taken off: a line bending into the drum all at once about its middle, on the scroll and then snapped ("it bends on both sides"); all four waiting for the whole sentence then rolling one by one; a belt round a shrinking racetrack (the text piled up). Each line's ink hands over to the panels over the first `HAND` .05 of its coil while the snake holds still (it used to move during the crossfade, and the line looked doubled for a moment: owner, "they transition into something before bending"); the canvas lies over the rings, so a line still flat shows the canvas and never the panels' joins; its ghost trace fades out, and the ring tilts to −7° about its own front line. It turns at 66/87/75/96s a turn (1.5× the first drum's 44/58/50/64, at the owner's asking), front moving left, easing up to pace over 1.2s, and stops only off screen or once the stripes have covered it. While coiling, a ring's panels are laid again every frame (about 80 a ring); closed, only the ring turns. A waiting ring's panels lie flat on its written line at opacity .01 under the canvas, and the drum is put up so as the writing starts, so the pictures are on the GPU before they take over (put up on first sight, they cost a frame). **The drum can be taken in the hand, as the About cards can** (owner's asking, 2026-09-29: "move them like how I move my cards"; a fine pointer only, once a ring has closed; `cursor: grab`). A mouse over it leans it toward the pointer, eased a tenth a frame as the cards' tilt is: the side under the pointer goes back (`rotateX` up to `LEAN_X` 5°, about the drum's own axis, `transform-origin` z −R) and the eye swings round with it (`perspective-origin` up to `LEAN_O` .12 of the block's width). Grabbed, the closed rings turn 1:1 with the hand, each on its own spring after it (`KS` .16/.12/.095/.075, top tightest, damping .8, after the cards' k .06 and .82), so they twist a little and settle, and their own turn holds while held; let go, the hand's speed carries on and runs down (`GLIDE` .94 a frame; a hand still for 90ms throws nothing), then each ring eases back up to its own pace. Measured: a 290px drag turns it .78 rad, the throw carries it about .7 rad more and settles within a second, 60fps throughout. **The hearth** (owner's asking, 2026-09-30: "add some button inside of it and when I click it'll lighten up like гал голомт"; then "remove the button: when I hover the drum my cursor changes to fire, and when I click it'll fire up"). Once all four rings have closed (`.tz.is-closed`), the cursor over the drum is a flame (cursor.js), and a click on the drum (a press let go within 6px and 500ms, so turning it by hand never counts) — "over the drum" being its own outline, not its text block, which is ~150px a side wider at 1440 (owner: "when I stop hovering, bring my cursor back"): `onDrum()`, the radius seen at the axis's depth through the 2600px perspective, plus 8px, across, and the lines with the rings' tilt (.13R) above and below; it sets `.wr-t.is-over`, which the flame cursor and the click go by — kindles a fire at its heart, across on the axis and down between the second and third lines (`placeFire()`, `--fx/--fy`); a second click puts it out, and it goes out if the rings unroll. **It lights itself if nobody clicks** (owner's asking, 2026-11-14: "if user ignore fire sign light up fire immediately then show next section's transition"): scrolled `AUTO` .3 of the way into `SPIN` (1.075 screens from the pin) with the rings closed and no click yet, it kindles (`autoFire()`; if the rings close only after that point, it kindles as they close), so the stripes always rise over a lit hearth; scrolled back above that point (a hundredth less), a fire it lit goes out again. A click, lighting it or putting it out, is the visitor's own and is left alone until the rings unroll. Measured at 1440×900: unlit at 1.05, lit at 1.1, out at 1.0, lit through the stripes; a click's fire or darkness holds either side of the point. **The stripes wait for the fire, then `WAIT` 4.5s more** (owner's asking the same day: "after LIGHT UP scroll 4-5s then GO TO NEXT SECTION"; a scroll gap of .35 screens after the fire was tried first and was too short). In time, not scroll: until the fire has burned `WAIT` seconds (`litTime`) the stripes keep just ahead of the scroll; then they start from wherever the scroll is (never before `HOLD`), or regardless once the scroll is `MAXD` 4.5 screens past `HOLD`. That place is fixed (`startAt`) and the section is cut to end where they close (`fitHeight()`), so no covered screen is held; until then it is long enough for the most it can wait (1 + HOLD + MAXD + RUN, 9.78 screens). The fire going out (scrolled back above `AUTO`) frees `startAt` again. Every section below reads its place live, so the changing height is safe. Scrolled past `AUTO` before the rings have closed, the rings close in `UP_FAST` .8s rather than `UP` 3s, so the fire can light first. Measured at 1440×900, steady scrolls: 300px/s, lit at 1.23 screens from the pin, stripes 4.7s later, section ends 5.41 as they close; 900px/s, lit 1.82, stripes 4.4s later, ends 8.78; stopped at 1.8 to watch, the next scroll after 4.5s starts them where it is and the section ends at 4.53. A click there tosses no шагай; a drag from it still leaves their trail. The fire (`.tz.is-lit`): one light layer over the pinned screen in colour-dodge (`.wr-fire`, over the screen and not in `.wr`, whose isolated group turned a dodge over nothing into an orange blob), so the black stays black and only gold takes the fire (the letters amber to hot yellow, the хана near it embers); the inner walls seen through come up from .3 to .62; a small screen-blended haze (`.wr-glow`) is the fire's own light; it flickers by opacity and transform only (`wr-flick` 2.9s, `wr-lick` 2.3s); it kindles in 1.5s and dies down over 2.2s. 60fps lit and turning at 1440×900. Tried the same day and taken off: a round button with a drawn flame at the drum's heart, and lighting on hover alone. `index.html?debug` exposes `window.__drum.pose(ring, f, S)` to hold a ring at a moment of its coil, and `release()`. Timing, in screens of scroll: the writing starts .35 before the pin (`LEAD`), as the screen comes up, and takes 1.2 (`PLAY`); the full drum turns for .75 (`SPIN`, .45 until the owner found the stripes came in too fast) before the stripes start (`HOLD` = PLAY − LEAD + SPIN), so the section is about 4 screens tall. Apart from the turn, nothing moves on its own. Each line is lifted .295em in its 1.18 row, because the face keeps .6em of empty ascent over this sentence's ink (measured at 100px: ink .84em over the baseline, .26em under). Without the script or the font, on a narrow screen or with reduced motion it is the finished sentence in gold, still, and nothing pins. Measured at 1440×900: a steady 60fps through the whole section at 400 and 1200px/s of scroll, and while the rings snap and turn. Tried before it on 2026-09-29 and taken off, don't bring back unasked: the same sentence as the two pictures in it (a spring line welling up through a rippling water line, then a mountain of its six words stacked 1-2-3 rising through a ground line; the owner: "nvm lets try step2"); a marquee of the sentence on a flat gold ribbon (#b08a45, white bichig; it replaced "Research ✣ Design ✣ Test" and a vertical-column setting); the sentence on a turning drum of its own (four rings of the clauses A, B, A, B with ✣ between copies, turned by CSS; the rings above are its heir, rolled up from the written lines); that drum shaped as a гал голомт, first as CSS-built 3D iron ("it looks so bad"), then a gold line drawing, then wrapped round the owner's AI render of an iron fire basket ("i dont like it"; the render and its cut-out are in `art/site/_source/golomt*`; the drum's code is in git history only if committed, else gone). The screen sits just under the bar (`.tz-pin` padding-top `clamp(64px,8vh,80px)`; About's `.ab-wrap` bottom padding 40px). The gold clouds are decoded a screen and a half early, since decoding them on first sight cost one 316ms frame. Made smoother the same day (owner: "make it more smooth"): each stripe is a window with a door that slides up while the ground inside slides down by the same amount (`.tz-s` > `.tz-d` overflow hidden > `.tz-g`), all transforms, so nothing repaints (it was a clip-path that repainted five screens of clouds every frame); each stripe eases in and out of its run (sine; theirs are linear); and with Lenis the transition and the timeline draw in Lenis's own scroll callback, the same frame the page moves, not the next. Measured with trusted wheel events: stripe lag 0px, the ground inside the stripes moves 0px. Then the work in order (below). Removed on 2026-09-29 when the owner picked the timeline over it: a Selected work band after trionn.com (`.tr`: half-screen case panels slid sideways, 0.35px a pixel of scroll, cards rising into line, a Mongol-bichig digit rail, gold clouds held still behind; it took about 10 000px of scroll and showed the same cases, and Playground and the only landing link to work.html went with it). The last copy with it is in the session scratchpad only; git has none. The work in order comes straight after the transition, after designxhand.com/experience's agenda ("Pre-Event / After Hours"; `.tl`, 2026-09-29, the owner's pick of that section's two parts): measured off theirs in headless Chrome, one screen held while a row slides left (theirs 0.9px per pixel of scroll, ours `RATE` 0.5), a thin wavy line along the row (a sine, `AMP` 22px, `PERIOD` 1700px, drawn as an SVG path in the script), one case on it at a time, arriving as designxhand's events do (owner's asking, 2026-09-30: "mine is so dull"): the line is lit behind a reading point at .62 of the screen and dim ahead (`.tl-lit`, a copy of the path in a window whose right edge moves, window and line counter-translated so it is all transforms, a 220px soft edge), and when a case's place reaches that point it gets `.is-in` (off again past .7 on the way back): a gold diamond lights there with a halo (`.tl-node`, a diamond so it isn't Experience's round dot), a hairline drops from it beside the words (`.tl-item::before`, scaleY), and the plaque, name and line rise in 22px, staggered .1s, on CSS transitions; the pictures follow designxhand's stack and micro-motion, measured off theirs (owner's asking, 2026-09-30): two frames per case to the right of its place, the case's cover and its low-fidelity drawing (owner's asking, 2026-09-30: "show their first pic and their low fidelity"; NetPay's and Voice's are the `svg.lofi` drawings of their case pages, captured whole and flattened to `art/netpay/lofi.webp` 1600×823 and `art/voice/lofi.webp` 1600×1182, originals in `art/<case>/_source/lofi.png`; OhayoFX and HUB have no low-fi, so they keep two screens each; for a moment the user flows were shown instead, their captures are kept in `art/<case>/_source/flow-landing.png`), rounded 12px with a gold hairline and a deep shadow, the upper one lifted more (the owner's "give me radius"; designxhand's are square), the low-fi drawings framed at their own proportions and zoomed only 1.04 so the pan barely trims them; sized for a 900px-high screen ( scaled with the screen's height, `K` .78–1.2, from `data-dx/-y/-w/-h`), overlapping, the bigger on top (`data-z`) and crossing the line, the words under the line clear of them (checked along the whole row at four sizes); as a frame crosses the screen it drifts from p to −p (`data-p`, ±25 or ±70) and the picture in it, held at `data-s` 1.2 or 1.25, pans the other way across its room (all of it at 1.2, .6 of it at 1.25, theirs exactly), straight with the scroll; no zoom change, no hover; cases 1100px (or .76 of the screen) apart; 60fps measured at 500 and 1200px/s (no dates since 2026-09-30, at the owner's asking: with them it looked like a second Experience, and the dates are there; HUB's "First UI/UX project" sits under its line, `.tl-note`), a discipline plaque — `.tl-chip`, after designxhand's "Inner Circle" badge at the owner's asking ("use exactly this"); theirs is a PNG with its words baked in, ours is drawn in CSS: scooped corners (four masked circles), brushed gold with a fine brown tooth, engraved dark-bronze serif caps, a flourish drawn for it at each end — the name linking to its case page, a line of copy), two pictures per case (see below for their stack and motion). **It is "Recent work", about the projects, not the companies** (owner's asking, 2026-09-30: "keep Experience and My Work, change them to recent works and focus on project not company"; About's Experience tells where): the four case studies newest first, NetPay V2 (2025–present), Voice mini app (2025), OhayoFX (2024), HUB ("First UI/UX project", its page's own words), and each project's name is the largest thing on the line (`.tl-t`, `clamp(32px,2.8vw,42px)`; it was 30px). Until then it ran oldest first as "From the first project to now", with a big italic chapter heading top left naming where each was made (First project / CSKIT / NetCapital); that heading is gone, don't bring it back. The intro "Recent work" (sub: "Four case studies, the newest first.") sits near the screen's head (`.tl-intro` top `clamp(74px,9.5vh,96px)`), so it shows about 126px of scroll after the transition's stripes close (it was mid-screen, 310px of empty clouds first; owner: "reduce the empty space"); it fades out as it slides off, gone by .36 of a screen. The ground is the transition's gold clouds carried on (the stripes' tile sits on that screen's foot and this screen starts where it ends, so `--tl-cy` is 0 and the grain `--tl-gy` −one screen; no seam at full resolution) and held still. Pinned only on a wide screen with motion allowed (`.tl.is-on`); otherwise a stacked list with the pictures in a row. **Contact, the landing's last screen, is laid out after milancompain.com's** (`.ct#contact`, after How I Work; owner's asking, 2026-09-30: "copy this web's contact section"), measured off theirs: one screen, centred, a line in the italic serif ("Have something in mind? Let's build it together.", ours), the address large in Golos 700 (`clamp(20px,3.3vw,48px)`: 47.5px at 1440; it was `clamp(22px,4.6vw,70px)` until the owner asked for it smaller), "Click to copy" under it, and a credit at the foot ("© 2026 Мөрөнгуа · UI/UX & Product Designer · Ulaanbaatar"). A click on the address copies it (`navigator.clipboard`) and "Copied ✓" comes up over it in gold for 1.8s; where the page can't copy it opens the mailto. Over the page's own ground 56 gold motes laid from a fixed seed twinkle slowly, six of them large and soft (opacity only; still under reduced motion; theirs are green stars). Under the hint, as theirs, a row of social links (`.ct-soc`: Instagram · LinkedIn · GitHub · Telegram, 10.5px caps at .28em, .55 ivory, dots at .35, gold on hover); they and the address lean toward the cursor as theirs do (cursor.js `MAGNET`, as the bar's links). The owner's profile URLs are still owed, so each is a placeholder (`href="#contact"`, `data-todo`) that stays on the screen; never link theirs. The bar's "Let's talk" glides to it. **How I Work was taken off the landing on 2026-11-15** (owner: "rmv how i work"): its section (`.hw#how`, the six steps over the 3D models played on a canvas), its style and script, the bar's link, the case pages' footer links to `index.html#how`, and the sideways slide that carried Recent work into it (`SLIDE`, `slideEase`) all went; Recent work now ends with its row and Contact follows straight under it. Its 302 frames moved to `art/_archive/how-i-work/`, unserved; the last code is in the GitHub repo's copy from before that date. Don't bring it back unasked. **The bar is laid out after benjamincreative.me's** (`.onav`, owner's asking, 2026-09-30: "copy this one's nav bar, and remove ours"; the old one was a dark blurred strip of small gold-lit caps): no ground of its own, "Portfolio" at the left, About and Work in even columns from a third of the way across (theirs measured: 32.5%, then 14.7% each; ours land within 2px of theirs at 1175px; How I Work was the third until 2026-11-15), "Let's talk" at the right (a mailto to the footer's address until Contact came, now `#contact`), 15px Golos 500 at .75 ivory, the lit section full ivory. Each name rolls up on hover: letters split by the script (`.roll i`, the word kept whole in a `.sr` for screen readers), each carrying its copy one line below as a text-shadow, rising a line 18ms apart over .55s; fine pointers only, none under reduced motion, plain text without the script. Their small grey marks are ours in bichig digits ᠑ ᠒ ᠓. It passes clicks through where it has no link. Over About's cream card a link turns dark ink (`.is-light`, the bar's scroll check tests each link's centre against `.pass`; it looks at the sections straight under `.one` and those in `.abx`); a difference blend was tried first and left the bar unpainted over the chest's layers. `--nav-h` is now `--nav-pad` + 30px (58px at 1440, the old bar's 59.8), so the rows under it keep their place. Below 861px the columns close up; below 561px "Portfolio" goes and the rest fit in one row at 375. **The first screen** (owner's brief, 2026-09-30, phase 1 of a landing redesign on branch `landing-redesign`): the bar is up from scroll 0 (it used to come down with About) and is first in the document, so Tab reaches it first; the chest rests in the band between the bar (its height + 16px) and "Scroll to open" (`measureBand()`/`restRect()`), so no text sits on the painted border (a labels row under the bar, Since 2018 · Ulaanbaatar · Open to work, and a Sound off/on toggle beside it sat between them until the owner took both off on 2026-09-30, "rmv them"; the toggle was the only way to play the chest's opening sound, which browsers allow only after a click, so the sound went with it and `chest.m4a` is kept, unserved, in `art/hero/_source/`); on a portrait screen it rests cropped to the lion medallion (`CROP` .52 of the frame's width) and the dive opens out from there; the footer has 16px sides and stacks on a phone, with "Skip intro" (jumps to #about and takes the focus) in the right corner. A real `<button id="latch" aria-label="Open the chest">` covers the painted hasp (`HASP`, placed from the rest rect by `layout()`, which also sizes the canvas); click, Enter or Space glides to p .52 (`OPEN_AT` = `F1`, the board fully down with the push-in under way; it was .56, a held-open beat, until the push-in moved up to start halfway through the opening on 2026-11-11, `Z0` = (`F0`+`F1`)/2) in 1.8s with Lenis (jumps under reduced motion, goes to About without GSAP); it is disabled once the lid moves. A name tag hung from the latch (a little pass card with Мөрөнгуа and the role, on a gold cord) was tried the same day and came off at the owner's asking ("rmv this"); don't bring it back. Frames load in two goes: f000, then `FIRST` (1, 2, 3 and every seventh), the rest once the page is idle after load or at the first scroll, key, touch or click; `render()` draws the nearest frame below, else above. |
| `index-v2.html` | a copy of the landing (2026-11-21, owner: "duplicate this web, remove everything but my name paiz and chest"): the chest and About (the name card on its star sky) only; Experience, Recent work, the quote and Contact, the `.abx` wrapper and the bar's Work and Let's talk links are gone. Same art, fonts, tokens.css, about-motion.js and cursor.js as the landing, and its inline style and script are the landing's as of that day (rules and code for the removed sections stay but find nothing and skip). It is a separate page: changes to `index.html` don't reach it. About is one centred full screen there (the card in the middle of the space under the bar). Its sky is a planetarium view (owner, the same day, after a Stellarium-like screenshot: "when I click on stars they show their name"): `.sky-cv`, a canvas painted once per size from a fixed seed (a Milky Way band down the left with dust lanes and its own crowd of stars, kept faint since the owner found it "catching too much attention" (glow .017 and .02, its stars at .16–.46), ~700 field stars and 40 brighter ones in white, blue-white, warm and orange), so nothing drifts behind the words; over it the stars of Mongolian tradition as `<button class=sky-pin>` in % of the sky (Алтан гадас, Хөх морь and Цагаан морь, the seven of Долоон бурхан, Мичид as one cluster, Гурван марал, Цолмон, and Тэнгэрийн заадас as an invisible hotspot on the band), clear of the card. A click or Enter shows one label (`.sky-tip`: the Mongolian name, the Western one, a line on its meaning; below the star in the sky's top third, kept inside the screen); a click elsewhere or Escape closes it; buttons throw no шагай. "Click the bright stars" sits top left. The lore lines are short and hedged; tellings vary, so check any with the owner before they grow. `.ab-wrap` passes clicks through except over the card and its note. The sky is a still backdrop fixed to the screen there (owner, the same day: "remove the dark space between chest and name card, make the star bg static"): `.ab-sky` is `position:fixed` and fades in on the chest's timeline with the blackout (`fromTo` opacity 0→1 at 70–86, toggling `.is-up` past .5, which lets its stars take clicks), so the chest gives way to the night sky instead of black; `.one` is transparent, its хана and grain and About's fade-in are off, and About starts 64vh up (16 more than the landing) so the card begins to rise just as the sky is fully up, then settles in the middle at the page's foot. Without the scroll rig the sky is About's own background (`position:absolute`), so it never covers the shut chest. **Then repainted warm and stylised** (owner's pick after a critique the same day: the photographic sky, cool and blue-white, clashed with the painted chest and the paper card): a warm black (#080604 → #020101), a faint gold light behind the card, the Milky Way only as a soft gold wash (no dust lanes, no crowd), ~380 stars in the site's ivory and golds only, 14 brighter ones as four-pointed sparks (the site's diamond with points), and the figures joined by fine gold lines at .32 as on a hand-drawn star map (Долоон бурхан's ladle with its bowl closed, Гурван марал's belt, and Хөх морь and Цагаан морь dashed to Алтан гадас as their tethers); the star buttons are ivory and gold too (no blue). So the photographic description above is the first version. Over the sky, film noise after React Bits' Noise (owner, the same day: size .5, fps 23, opacity .16, scanlines .1): `.sky-noise`, grain one device pixel fine, 23 times a second one of eight 256px tiles made once laid at a random offset, at .1 (.16 at first; "a little bit less"), with `.sky-scan` lines at .06; the sky's ground went from a blue-black #05070e to a neutral #020203 → #000 at the same time ("bg looks too blue, make it darker"), and the Milky Way's haze to a neutral grey; it runs only while the sky is up and the tab visible, and holds still under reduced motion. It is moving grain, which the Motion notes say once made the owner sick; it went in at their explicit asking, so if it bothers them, freeze it (`still`) rather than remove it unasked. It ships with the deploy as a public URL unless `.vercelignore` lists it. |
| `index-v3.html` | a copy of index-v2 (2026-11-21, owner: "the stars and the name card don't look good together, be creative") where the sky is a printed star chart: chart paper (#0a0907) lit from the top left like the card, gold rings and twelve hour lines drawn out from Алтан гадас at the head of the screen, a graduated outer ring, ~170 printed dots (no glow), and the figures with their names set in the serif as part of their buttons; laid out from the card's resting rect so it frames the card at any size (figures that don't fit beside the card are left out). The noise holds one still frame, no scanlines; the card has a short shadow down and right; its gerege was toned down (saturate .68, brightness .9) and read "too grey" to the owner, so it is warm gold again: sepia .22, saturate 1.08, brightness .96, contrast 1.03. The card's gold-leaf spine there is full gold too (owner: "make it more goldish"): `.pass-leaf` at full opacity with no desaturation (it was .7 and saturate .75, which read pale over the paper), its gradient warmed to #f2d78a → #a7803a to sit with the gerege. Its footnote went into the card under Товчоор for a while and came back under the card the same day (owner: "I kinda don't like it in the card"); the chart counts the card and its footnote together (`foot`), so the outer rings and the hint pass below the footnote's words. The layout reads layout boxes (`offsetTop` up to About), not screen rects, since the card is still moving in its entrance or leaning under the pointer when it runs, and allows for About being taller than the screen on a phone (`shift`). A star's label is moved to `<body>` by the script and is `position:fixed`, z-index 45, so one that opens over the card shows above it (inside the sky layer it opened behind the card); "Click a star to read its story" sits under Алтан гадас's name when the band over the card is at least 84 × k tall, else centred in the strip under the card (a phone), else hidden. Checked at 1536×730 and 375×812: no sideways scroll, no console errors; on a phone only Алтан гадас and its two horses fit beside the card. **Experience is its third section** (owner, the same day: "add third section with camel n mouse and work exp"): the landing's `.ex#experience` (the тэмээ and хулгана stage, the mouse's 12 жил dialog, the work list, its full-screen hold at 150vh), straight under About with no `.abx` wrapper, but **without the torn edge or About's hold and dim** (owner: "remove that scroll animation, make it static", then "rmv that paper cut"): About is not sticky, and `.ab-dim`, the tear's markup, style, masks and script and the stick/dim script are gone from v3; Experience follows on a plain straight edge (the owner will make the transition there). **The sky scrolls away from About's foot** (owner, the same day: "when i reach section 2's bottom scroll the bg"): it is fixed only until About's foot reaches the screen's foot; there the script flips `.ab-sky.is-parked` (absolute at About's foot, `--sky-h` the screen's height, the same place on the screen at that moment), so the chart, its stars and the card scroll up together with Experience right under them; scrolled back up, it is fixed again. Only the class flips; nothing is set per frame. **The animals' side is the star chart's ground without its rings** (owner: "have same bg as galaxy in camel n mouse", then "no rmv rings just give same bg color", then "make them same color"): the sky is not flat #0a0907 (its script lights it from the top left, darkens its edges, and a grain one device pixel fine lies over it at .07), so flat #0a0907 read darker and smoother at the seam. `.ex-l::before` lays the sky's two gradients over `--night-100`, carried on from the sky's foot (the script sets their centres and radii, `--gl-*` and `--vg-*` on `.ex`, in the ground's own box: 100vw left of `.ex-l`, one sky's height below the sky's top), and `.ex-grain`, a canvas the noise script fills with the sky's own grain tile at one device pixel a grain, at .07 (a CSS tile of it was tried first: resampled at a 1.25 pixel ratio it came out softer and read darker, and the owner saw the seam: "can u mix them well"). The chart's rings, dots and figure lines fade into the bare paper over the sky's bottom fifth (the foot of `paint()`), so nothing stops at the edge. Keep the side's gradients in step with `paint()`'s `ground()` if its light or vignette changes. The light needs eight stops in CSS, not two: the canvas fades it to `rgba(0,0,0,0)` unpremultiplied, so it falls off as .07 × (1 − t)², while CSS interpolates premultiplied. A two-stop fade left the side ~2.5 levels brighter and yellower than the sky's foot, a visible seam (owner, 2026-11-21: "the colors don't match"). Measured after the fix at 1536×730: 17.6 above the seam, 17.4 below it. No dots, rings or figures; a chart canvas with rings drawn out from the camel was tried the same day and came off. An open star label closes once Experience comes up over the sky (it floats on the top layer). Checked at 1536×730 and 375×812: no sideways scroll, no console errors. **The work list is a register** (owner, the same day: "i don't like it at all, i want something luxury, easy to look at, do more research, and don't contain too much content in exp"). Two versions came off first: an expandable ledger (one row open at a time with the period, the owner's line on the work, case-study links and NetPay V2's +10.0%; researched against Awwwards experience sections) and, before it, the row list with "Peek" chips. The register follows the quiet-luxury conventions the research agreed on (restraint, one focal point, generous space, a light serif, small tracked capitals) and Aman's lists (a tiny capitals label, a light serif title, one short line): centred in the right column under a gold `Туршлага` kicker (`.ex-k`) and the italic heading, each job three lines — its years in traditional Mongolian digits as a small gold ornament (`.ex-bn`, `lang=mn-Mong`, aria-hidden, generated from code points U+1810–1819), the company in Source Serif 4 at 300 (`.ex-t`, 54 × --ui), and the role with the Latin years in tracked capitals (`.ex-c`, 12 × --ui, ivory-200, a gold diamond between, the years are what a screen reader reads) — with short gold rules between jobs. Nothing opens, links or moves. Tracked lines carry a left pad of their own tracking so they centre on their letters. In Noto Sans Mongolian ᠑ looks like a Latin 9 (+᠑᠐.᠐% read as "+90.0%"), so never set a claimed number in bichig without a Latin version as large as it. The 12 жил dialog's kicker is ᠑᠒ жил and its count ᠑ / ᠑᠒ with a visible "1 / 12". On desktop the column sits in `clamp(32px, 5vw, 96 × --ui)` from the split's hairline and `clamp(16px, 3.3vw, 64 × --ui)` from the right (owner: "it's nailed in both sides"); it fits the held screen at 1536×730 (119–660), 1280×720 and 1920×1080, and on a phone it is the same register at 38px names, 24px from each edge. **Then made ivory-only and left-aligned** (owner, the same day: "drop the yellow color on the headings", a palette from the design system, revamp the right side, the left stays): no gold in the register at all. The kicker is `label` in ivory-300, the years are in their own 150 × --ui column on the name's baseline, in traditional Mongolian digits (`.ex-y .ex-bn`, 20 × --ui, ivory-300, aria-hidden, the Latin years in a `.sr` beside them; owner's asking the same day), the names Source Serif 4 300 at 44 × --ui in ivory-100, the roles GIP 16 × --ui in sentence case in ivory-200, and the rows have ivory hairlines at .12. It sits in a 680 × --ui block (`.ex-reg`) centred in the column. The bichig years, gold rules and diamonds came off the rows, and the хана veil behind went from .93 to .96. On a phone the years sit above the names, which are 34px. The 12 жил dialog keeps its gold and its bichig. **Third pass, after auge-xp.com/about's awards list** (owner, the same day: "creative yet traditional", "it feels soulless"). The register runs across the column (`.ex-reg` 900 × --ui) as rows of years | company | role, the role right-aligned. The heading has a count beside it (`.ex-n`: a bichig ᠓ in ivory over "3 roles"). Each year is a bichig line over a Latin one (`.ex-yl`, visible, so everyone can read the dates). Desktop sizes are the design system's full sizes: labels 11px (13.75 × --ui), roles 16px (20 × --ui), names 41.6px (52 × --ui). Theirs, measured: rows rise 24px and fade in one after another while their words scramble, and on hover a solid band slides up from the row's foot and the words invert. Ours: once the list is a third in view, rows rise 24px (.9s, .14s apart) and every word scrambles into place left to right. The bichig years scroll through ᠐–᠙, Latin through digits and letters of its own case, with new letters every 45ms. The band is the name card's paper (`--paper-100`, `.ex-item::before`, translateY only), and the words go to ink through a difference blend inside each row's isolated group. Hovering a row also re-scrambles its name. Hover is for fine pointers only. The entrance is off under reduced motion, and without the script the rows are just there (`.ex-list.is-anim` is set by the script). **Then the motion came off** (owner, the same day: "remove animations"): no entrance, no scramble, no paper band, and the script, `.is-anim` and the blend are gone. The register is static again. In the same change: names at weight 400 (owner: "bodyweight"; it was 300), `Туршлага` back in `--gold-500`, the bichig years larger (34 × --ui, 27px on desktop; 28px on a phone), and the Latin years under them smaller (11 × --ui, 8.8px on desktop; 10px on a phone). The register is otherwise ivory. |
| `work-netpay.html` | NetPay V2 — the deepest one, 8 sections |
| `work-voice.html` | Voice mini app |
| `work-ohayofx.html` | OhayoFX |
| `work-hub.html` | HUB — NetPay/Voice layout (`.step.wide` + `.annot` rows); four roles in chain order, and its own chain section (`.hb-chainsec`, s02) |

**Removed on 2026-09-30, at the owner's asking** ("rmv them"): `work.html`, `how-i-work.html`, `playground.html`, `about.html`, `contact.html` and the unlinked draft `how-i-work-3d.html`, with the 690 turntable frames only the draft used and the 10 pictures only those pages used (how-i-work's masthead and step SVGs, `art/steps/`, and the gallery's placeholder `hero.svg` tiles). The site is the landing and the four case pages. Their links now go to the landing's sections: Work `index.html#work`, About `#about`, and each case page's back link ("Сонгосон ажлууд", OhayoFX's "Selected work", "Works", "All work") to `#timeline`, the Recent work list; Playground and Contact links came off, and so did the landing's "See the full process →". Contact came back later the same day as the landing's last screen (`#contact`). The last copies are in git history (commit 0ed4c46 of the old `portfolio` repo). Don't bring them back unasked.

**New structure, foundation laid 2026-11-21** (owner: the old About/Experience "too empty"; the plan is chest → name tag on a star sky (Алтан гадас game later) → Experience 40/60 (тэмээ and хулгана start the 12 жил game) → Recent work → Chinggis Khan's words in bichig → Contact; the games' plan is in Claude's memory, `lore-games-plan`). Done so far: About's хана is covered by a night sky (`.ab-sky`, over the fade-in, fading into the хана at its foot): 110 seeded gold stars twinkling as Contact's, and Долоон бурхан with Алтан гадас (`.ab-const`, an SVG at the top right, static, with an "Алтан гадас" label), hidden under 861px. The old Experience timeline (`.xp`: line, diamonds, bichig years, lit cards) and the Scroll cue are gone, markup and style; about-motion.js skips its Experience part when there is no `.xp`. In their place `.ex#experience`, a 4fr/6fr grid: left a sticky stage with placeholders for the owner's тэмээ and хулгана art (`data-todo`), the mouse a button that breathes a soft glow and opens `<dialog id=ex-dlg>` ("You've entered the game… collect all twelve…", 1 / 12; text only, no game logic yet); right the work history after overworldaudio.com/work: an italic-free serif name, year, role and a ▶ Peek chip per row on hairlines (NetCapital 2025–26 Product Designer; MOT Forex LLC 2024; CSKIT 2024), the chip `aria-hidden` until the hover peek is built. On a phone it stacks and the chips hide. Before Contact, `.qt`, a placeholder screen for the quote (`data-todo`: the owner gives the bichig text and its Secret History source; never invent one). New rules size with `calc(N * var(--ui))`, and `--ui` is 1 at 860px and under. Then (owner, the same day): the left column is the animals' own dark ground (`.ex-l::before`: night with a warm glow, out to the screen's left edge, a gold hairline at the split; on a phone a full-width dark band above the list), the right keeps the хана, and the list grew (names 48, year and role 22, the heading up to 68, the chip 13, all × --ui; year column a fixed 120 × --ui, nowrap); `.ex-in` may run to 2000 × --ui wide so nothing wraps at 1536. On desktop (861px and up) Experience is held full-screen (owner: "hold it full-screen"; transitions in and out are the owner's to add): `.ex` is 150vh and `.ex-in` sticks at 100vh, so the dark left side fills the screen for half a screen of scroll; the stage and the list each take the full height under the bar. While held, the page's хана kept scrolling behind the still words and made the owner motion-sick (2026-11-21), so `.ex-in` carries its own хана (at .07, baked as a .93 black veil over the tile) and grain (.1) on `::before`/`::after`, out to both screen edges, still with the held screen. Any new pinned screen needs the same: never pin words over a ground that scrolls. **The torn edge into Experience** (owner, the same day, after shopify.com/editions/winter2026): Experience's own grounds (`.ex-in::before/::after`, the хана and grain, now at every width, and `.ex-l::before`, the dark) reach `--tear-h` (130 × --ui) up into the About sky, their tops masked to one ragged line drawn once by the script from a fixed seed (three scales of eased noise and a few deeper torn fibres), so the rip is in the real grounds and nothing seams; the mask is an SVG data URI on `.ex` (`--tear-mask`, `--tear-w`, and `--tear-x`/`--tear-xl` placing it, since those boxes start 100vw left of their elements), redrawn on resize. Along it a pale fibrous rim (`.ex-tear-rim`, #d8cebb under the grain, 1.2–3px with the odd thicker fibre) with a soft shadow up onto the sky. Static. About's wrap ends 130 × --ui lower so the rip clears its footnote. **Its motion** (owner: "add its animation"; measured off Shopify's: their picture holds still while the torn paper rides up over it and dims as it goes under; the tear's shape never changes): About and Experience share a box, `.abx`, and About is `position:sticky` with `top` = `--ab-stick` (the screen's height less About's, never above 0, from the script and a ResizeObserver), so once its foot reaches the screen's foot it holds still until Experience ends, and Experience (z-index 3) scrolls up over it, tear first; `.ab-dim` darkens About from 0 to .65 as Experience's top climbs from the screen's foot to its head (scroll and Lenis's callback). At every width; the ground under the words never slides while they hold.

**Design system** (2026-11-21, owner's asking): https://claude.ai/artifact/4hSM5YdfgCKTMqXRcgBctU, a Design System artifact (tokens, type scale, spacing, radii, shadows, eleven components with guidelines, the хана/grain/cloud/hee patterns and the gerege and шагай). Its decisions: Source Serif 4 for display, GIP for reading at 16 (`lead`) and 14px (`body`) only, Golos for the bar, tags, the Contact address (500, not 700) and two caps styles (`label` 11px .2em, `micro` 10px .28em); one section-heading style (56px italic ivory); case pages share a night-and-gold header and keep their own accent inside; OhayoFX keeps its costume under that header. `tokens.css` (repo root) holds its custom properties only (`--night-000`, `--ivory-100…300`, `--gold-500/300/200`, `--paper-*`, `--case-<case>-*`, `--space-1…10`, `--radius-*`, `--shadow-*`, `--font-display/text/label/bichig`), generated from the system's tokens.json; every page links it first (`tokens.css?v=1`). New and migrated rules read these tokens; the older `--ab-*`, `--gold`, `--ink` on each page stay until their rules move over. Change a value in the system first, then regenerate `tokens.css`. Applied on the landing the same day (type): every small-caps rule is now `label` (11px 600 .2em: hero footer, Skip intro, Scroll to open, pass table labels, Experience dates and links, Contact hint, now in caps) or `micro` (10px 500 .28em: loader, social row, credit); GIP reading text is 14 or 16px only (`tl-d`, `tl-sub` 16; pass lead and values, roles, notes 14); Experience and Recent work share one heading (italic 500, clamp(40px,4.6vw,56px), ivory, no side rules); the Contact address is Golos 500 and its line full ivory. The pass spine keeps its engraved serif caps. Under 900px the hero footer row starts at the left so it clears Skip intro. **The landing is set at 80% on desktop** (owner's asking the same day, after viewing it zoomed out to 80% on a 1536px laptop screen): every content size in its style (the bar, the hero footer, About and the gerege, Experience, Recent work, Contact) was multiplied by .8 by script (hairlines of 2px and under, full-screen heights, vh/vw of 50 and over, z-index, letter-spacing and pattern tiles left alone; the pass card's eyelet and the gerege's hang point scaled together), `--nav-h` is now `--nav-pad` + 24px, and `:root` carries `--ui:.8`, which the Recent work script reads (frame size `K`, the gap between cases, frame offsets from the line, the row's tail). A block at the end of the style puts the reading text back at full size at 860px and under. So desktop text is small (labels 8.8px, body 11.2px): if a reviewer finds it hard to read, raising `--ui` alone won't undo it, since the CSS values are baked; scale them back by 1/.8. **The pass card** (both pages, owner, the same day): its corners are rounded, 14 × --ui (the top right cut corner went), and the хээ ornament is at .3 (was .49). **An Experience card lights with its diamond** (owner's asking the same day, "make it pop", after a React Bits scroll-blur reveal was tried and taken off): CSS only, by `:has(.xp-dot.is-lit)`: a gold edge at .42, a lit top hairline and a deeper shadow; cards not yet reached sit at opacity .5, but only once some diamond is lit, so without about-motion.js every card is full. One key phrase a card is `<b class="xp-key">` in gold-300, weight 500 (NetCapital: UX optimization; MOT Forex: visual identity). Then, the same day (owner): the cards' case links (NetPay, Voice, OhayoFX) came off, the column between the line and the year and card went from 48 to 112px (about 56px a side), and the cards lost their hover tilt and sheen in about-motion.js (v14); the drag and the strike on the line stay. The pass card keeps its own tilt and sheen.

`leaf.css` is the shared base; `work.css` holds everything case-specific and
loads on the four case pages. `index.html` is self-contained: inline style, no
`leaf.css` (its About carries what it needed from it).

**Scripts.** Scrolling is native on every page but the landing. A weighted wheel scroll used to
live in `scroll.js` and came out because it lagged a Mac trackpad's own
momentum; don't bring one back to the interior pages. **The landing is the
exception, at the owner's asking (2026-09-29: "when i scroll i feel dizzy and
things go bit blurry")**: `index.html` runs Lenis 1.3.23 from jsdelivr, the
version trionn.com runs, at its default glide (lerp .1) with the wheel at 1.5× since 2026-11-14 (owner: "scroll speed is too much, takes very long time to scroll down"; measured, a 10-notch flick goes 1500px where it went 800, 92% there by .5s; from 2026-09-30 it was lerp .075 and `wheelMultiplier` .8, "make scroll more smooth and slow", ~250 notches down the page on a 2560×1440 screen), wheel only (touch, keys
and scrollbar native; ctrl+wheel left to the browser), driven by GSAP's ticker
so the chest's scrub steps with it; off under reduced motion and without the
CDN script. Every scroll the page makes itself goes through `goScroll()`
(Lenis's `scrollTo`). Measured in headless Chrome at 1x on a trackpad-like
flick of 507px: same distance, peak 1 018px/s against native's 3 614, and no
frame-to-frame spike (native jumped 3 614px/s in one frame). At the rig's
default 2x the synthetic wheel reports half its delta, so Lenis looked to move
half as far; that is the emulation, not Lenis. If the owner finds it laggy on
a trackpad, the first thing to try is a higher `lerp` (.15).

- `scroll.js` — `work-netpay.html`, `work-voice.html` and `work-hub.html`
  (HUB takes the scroll reveals, the held phone screens and the skeletons;
  every other part checks for its page or its markup and skips). Gallery dots,
  the `.shift` ledger ruling itself in, NetPay ground, pointer field, Voice spark height, the
  scroll reveals on both case pages (`.rv-near`; hover lifts in `work.css` match),
  play/pause for the device videos, and the long phone screens (`.screen`,
  `.device.tall .screen-scroll`): on a fine pointer they get `.held`, so the
  wheel always scrolls the page and a screen scrolls by drag. As plain scroll
  boxes they trapped the wheel and stalled the page. Also the skeletons: any
  `main img`/`video` not yet arrived gets `.skel` (panel fill plus a faint
  sweeping band, `work.css` at the end), removed after `decode()` or on
  `loadeddata`. Static under reduced motion; unmarked without the script.
- `chart-hover.js` — the Outcome charts on NetPay and Voice: draws each at its
  box's measured width, wires the hover readout. Data is each page's own
  `<script type="application/json" id="chart-data">`; the markup keeps a static
  SVG per chart, drawn by this same code, for no-JS. The Outcome is `.oc`: a
  one-line finding, then a panel. NetPay: one hero figure (+10.0%) with its
  trend, then a before → after ledger (`.oc-row`) — a mixed result reads as
  failure if every change is set equally big. Voice: reach → depth tiles
  (`.oc-stat`, each number with its base), then the `season` chart (weekly
  users on the broadcast rounds, unlogged weeks hatched). Trends are `spark`
  specs with a fixed ±22% range around the before-mean, so tiles compare.
  Under the panel a segmented control (`.oc-seg`, bottom of `chart-hover.js`)
  switches Тойм and the tables — NetPay: Хүснэгт; Voice: Хэсгээр, 7 хоногоор,
  Викторин — with Motion's smooth-tabs motion measured off the example: the
  pill springs on a `linear()` curve in `work.css`, views blur-slide in the
  direction of travel. The views share one grid cell (inactive ones are
  `visibility:hidden` + `inert`), so the control never moves; without JS
  they stack. Every chart has its numbers in one of those tables. The old
  tabbed `.cbook` code in this file and `work.css` is unused now.
- `cursor.js` — the cursor on every page (see Conventions); self-contained, its style injected.
- `about-motion.js` — About on `index.html` (it runs wherever there is a `.pass-stage`); carries its own scroll listeners. Under the chest the card is far below the fold, so its entrance waits until it is scrolled to, and the tilt waits on the entrance. The Experience years (bichig digits) brighten as their row nears mid-screen but never grow: the scale-up came off at the owner's asking (2026-09-29, "I don't like how it gets bigger").
- Inline: `index.html` (hero; the only page with GSAP 3.12.5 + ScrollTrigger,
  from cdnjs, and it has a no-GSAP path: the shut chest as a title screen over
  the page; plus the bar, the transition with its bichig sentence, and the timeline), and `work-ohayofx.html` (the access counter: visits
  from this browser, in `localStorage`; dashes without it).

**Still owed by the owner** — placeholders, don't invent them: the email,
Instagram, LinkedIn, GitHub and Telegram URLs (Contact's social row, `data-todo` placeholders until then); NetPay's "Апп үзэх"
`href="#"`. There are no og tags yet; they wait on the production domain.

## Conventions worth knowing

**Gold is matte** (owner's asking, 2026-09-29: the gradient gold "is too AI-like",
"more matte"). `--ab-gold` is #c4a464, a matte yellow gold (the old #d8ad5c's hue, flatter;
#c9976b, the hero's tan `--gold`, was tried first and read as not yellow), and
`--ab-gold-hi` #d8c297, on `index.html`,
with every gold hairline and the хана tile in the same rgb(196,164,100). No
gold gradients clipped to text (the band heading is flat gold, Contact's title
flat ivory, the timeline's years flat gold), no gold glows
(the timeline's line and lit dots, the rail's mark; the one light on the site is the drum's hearth fire, and only while it is lit), and Contact's round button
is a flat disc. The pass card's foil spine keeps its leaf gradient: it is gold
leaf on paper, not type. The timeline's plaques (`.tl-chip`) are brushed gold too, at the owner's asking: metal objects, not gold type. At 10.5px, #c4a464 sits near 8.8:1 on black.

**The cursor is after milancompain.com's** (`cursor.js`, owner's asking, 2026-09-30: "nvm copy this cursor"), measured off theirs in headless Chrome and matched frame for frame: a 5px ivory dot that all but sits on the pointer (.9 of the way a frame) and a 28px 1px ring that glides after it (.14 a frame, settled in ~.7s), both in difference so they go dark on About's cream card; over a link, a button or anything draggable (`.gerege-hang`, `.xp-card.is-draggable`, the drum's `.wr-t.is-grab`, a case page's `.held` screens, whose grab hand is hidden with the native cursor) the ring eases to 1.57; pressed, to .92 of that with a matte gold rim (theirs green) and the dot to 1.39; the bar's links lean up to 4px toward it; moving, it sheds gold dust, a grain every 16px of the pointer's path and now and then a pair, 2–3.5px, 32 at most (it was one 3px grain every 26px, 16 at most, until the owner asked for "a little bit more"). **Over the drum the cursor is a fire** (owner's asking, 2026-09-30: "change my mouse when I hover this and show fire instead"; first over the hearth's button, then, the button gone, over the closed drum's own outline, `.tz.is-closed .wr-t.is-over`): the ring and dot fade out and a flame drawn for it sits on the pointer in a 52px round border on a dark disc, as the button had (owner: "add border to my fire button too"; the border gold, warm once lit), flickering (`cur-flick`, 1.15s, .8s once lit), gold, and orange with a pale core once the hearth is lit; pressed, it flares to 1.18; it takes the lit colour the moment a click lights the fire. Their "visit" bubble with its star is ours as a 76px ring reading "◆ View" on a blurred dark disc over any `a[href^="work-"]`. It injects its own style, runs only while something still moves, hides off the window, and rechecks what is under a still pointer on scroll. Fine pointer with motion allowed only; on touch or under reduced motion the system cursor stays. **A click on the ground tosses one шагай** (owner's asking, 2026-09-30: "I want шагай to appear when I click my mouse", with their sheet of the four sides; four a click until 2026-11-10, "only one шагай will appear randomly"): from the pointer it flies up and out spinning, lands 12–24px below on a random side, bounces once, rests and fades (1.5–1.8s; `.cur-shagai`, WAAPI, `throwOne()`). **Бэрх** (the same day): four throws in a row on four different sides bring up a note above the last, "Wow, you got бэрх!" with the four sides in it (`.cur-berh`, `role=status`, up as the fourth lands, gone after ~2.9s), and the count starts over. Only the ground tosses one (the same day: "only when I click on the background"): not a link or a button, nor a card, picture, plaque or words (`NOT_GROUND`: the pass card, the Experience cards, the gerege, the work's pictures and plaques, Contact's address and links, the drum). **Landing only**: none on the case pages (the same day; `cursor.js` returns before the шагай on any `work-` path), where the rest of the cursor stays. **Dragged** (the button held while it moves; the owner's asking, 2026-09-30: "when I drag I want them to appear constantly"), one hops off the path every 30px of it, a smaller throw (up 12–26px, 1.1–1.35s), so a drag leaves a trail of them, on the drum, the gerege and the cards too (a press there used to throw none). 22px tall (30 at first: "a little bit smaller"); 40 at most in the air. None for a click on a link or a button (`a[href]`, `button`, `[role=button]`, `[role=tab]`, `label[for]`, `summary`; the owner's asking, 2026-09-30: not when clicking the navigation or a case), nor a trail for a drag that starts on one. A drag over words still selects them, as it always did. `cursor.js?v=14` on every page. The хэт цахиур cursor drawn the same day came off for it (a traveller's fire striker turned so its steel's horn was the tip, with a strike version and sparks on click); its drawings are kept in `art/site/_source/cursor/`, its PNGs are in git history (c141a78); don't bring it back unasked.

**Motion.** Grain never moves — animated grain made the owner nauseous. The
slow light is a different thing and the owner wants it: NetPay's ground canvas
drifts (paced in time, not frames, so 120Hz screens don't run it double speed)
and Voice's `.vo-spark` runs down its lines on a 9s cycle. The spark moves by
`transform` (the masked `i` slides, its `::before` lines slide back), never by
animating `mask-position`, which re-rasterised the page every frame and
dropped ~145 frames a scroll.
Both were stopped once under a blanket "backgrounds never move" rule and put
back at the owner's asking on 2026-09-25 — don't stop them again to save
frames; both go still under reduced motion. The pointer field moves only in answer to
the pointer, and not at all under reduced motion. `scroll.js` and
`about-motion.js` leave the page readable if they never run; keep new motion
that way.

**Language.** `<html lang>` says which way a page runs. NetPay, Voice and HUB
are `lang="mn"`: body copy is Mongolian, and English section
headings and hero titles carry `lang="en"` so screen readers switch voices.
`index` and OhayoFX are `lang="en"`, and any
Mongolian inside them is marked `lang="mn"` (OhayoFX's
one block — the page is English; its Japanese is only inside the
screenshots, at the owner's asking).

**Case-page theming** is driven by four custom properties, declared per page
family and read by every panel on it:

```
--glass       panel fill
--glass-veil  backdrop-filter (or `none`)
--glass-hi    inset top hairline
--glass-lift  drop shadow
```

NetPay's live in `body.case-dark:not(.case-voice)` in `work.css`. The `:not()`
matters — Voice is also `case-dark` but has its own panels: `--glass:#0a0b10`,
`--glass-veil:none` on `body.case-voice`. That fill is the colour its old
`blur(16px)` frost measured on screen; the frost came out because re-blurring
fourteen panels every scroll frame made the page lag. HUB is
`case-dark` too, so the rule reaches it at (0,2,1); HUB's own violet set is
therefore declared on `body.case-dark.case-hub` (and `… .dark`) — equal weight,
later in the file. Drop the `.case-dark` there and HUB's panels silently turn
NetPay's `#202b37`. Change these four and the whole page turns together; do
not restyle panels individually.

Voice has no `.dark` wrapper, so it redeclares the `--np-*` and `--c-axis`
tokens on `body.case-voice`. If a component looks unstyled there, it is
probably reading a token only declared on `.dark`.

**Fonts.** Interior pages share one Google Fonts URL: Source Serif 4 (opsz +
wght, roman and italic) and Golos Text `wght@400..700`, one variable file, so
700 is real. Copy that `<link>` as-is onto a new page. The one exception is
`work-ohayofx.html`, dressed as a Japanese homepage of about 2002 (its own
`.oh-*` markup; none of leaf.css's header, paper or footer): DotGothic16 for
the chrome and headings, only at 16/32px so the dots stay on whole pixels, and
M PLUS 1p for everything else — the one Google Japanese gothic that also has
Mongolian ө/ү. DotGothic16 lacks them, so Mongolian never goes in it. Its
captures are cropped thumbnails that open full size; no inner scroll box. `index.html` takes the
interior URL too, now that About is under the chest. `--f-label` is Golos.

Noto Sans Mongolian loads only on `index.html`, as a
`text=` subset of the ten traditional digits U+1810–1819; on `index.html` the subset
also holds every character of the transition's bichig sentence (letters, the vowel
separator U+180E, ᠂ and ᠃). Google's text subset keeps the joining forms: the sentence
measured the same set in it as in the full font. A new traditional-script character
has to be added, URL-encoded, to `text=` on the page that uses it, or it falls
through to another font.

Body text on `use-gip` pages (NetPay, Voice, HUB) is GIP; the landing's About
names it directly on its reading text instead of using the class. GIP ships
five files: Light, Regular, Medium, SemiBold (300–600) and RegularItalic.
Nothing above 600 exists, so don't ask GIP for 700 — it comes out
synthesised. The other italic cuts are in `fonts/gip/_source/`.

**Images.** Every `<img>` carries intrinsic `width`/`height`. Without them the
page reflows for seconds after load and deep links land thousands of pixels
off. Keep doing this.

Any CSS rule that sizes an image by `width` + `aspect-ratio` also sets
`height:auto`; otherwise the height attribute beats the aspect ratio and the
image stretches (a 1600×2000 gallery tile would render 2000px tall).

Below the fold, `loading="lazy"`. Above-the-fold heroes are eager with
`fetchpriority="high"`: the NetPay and Voice covers, and the OhayoFX landing. HUB's four
phones under the title (`.hb-fan`) are eager without a priority.

Content rasters are WebP, most at their original pixel size (HUB's phone
captures are halved to 750px wide; `khadag`, `netcapital-building` and `gerege`
are cut down). Voice's ten phone captures ship twice, `-480` and `-900`, in a
`srcset`: a Voice screen never renders past ~226px, so 480 covers 2x (3x on a
phone) and the 900 is there for zoom; the 900s alone were decoding four times
the pixels shown. Encoding: `cwebp -m 4 -q 85 -sharp_yuv` for photos and screens,
`-near_lossless 60` or `-lossless` for design-system sheets. The original goes
in that folder's own `_source/` (`art/netpay/_source/`, `art/site/_source/` for the
landing's grounds, and so on; see art/ below). Left as-is on purpose:
`voice/system/{mark,nav-icons}.png`, `hub/sitemap.png`, `site/cloud-bg.jpg`,
and `netpay/cover.jpg`
(fallback in a `<picture>` of `cover-1100.webp` / `cover-2200.webp`).

The NetPay and Voice covers ride up over a pinned title —
`.hero-stack` plus `position:sticky` in `work.css`, no JS, static under
reduced motion. HUB shares NetPay's hero rules (eyebrow, title,
`.hero-desc`, spec row); its selectors sit in the same lists. Both are
16:10. NetPay's is a finished photo (4:3 file, cropped by CSS). Voice's is a
render of the phone on ribbed black (`voice/cover-{1100,2200}.webp`, exported
already 16:10 from `art/voice/_source/Purple Gradient Smartphone Mockup on Textured
Black.png`), with two still overlays on one ellipse fitted to the phone: a
spotlight on `.hero-plate::after` and a masked blurred copy (depth of field)
on `::before`, both eased with smootherstep over many stops — fewer stops
show a halo ring. A new cover means refitting that ellipse to where its phone
sits. Both plates must stay opaque in the middle, or the title shows through.
Earlier Voice covers are kept in `art/voice/_source/` (`cover-studio-*`,
`cover-cord-*`, `cover-keyart.webp`).

Videos never autoplay: `muted loop playsinline preload="metadata"`, with the
src ending `#t=0.001` so iOS paints the first frame. `scroll.js` plays a clip
near the viewport and stops it once it has gone; with reduced motion it gets
`controls` instead.

Phone screenshots go in `.device` frames, which expect roughly a 1500×3248
ratio (HUB's 750×1624 captures are exactly half of it; its taller ones sit in
`.device.tall`). HUB's captures carry their own notch, so the drawn `.island`
is hidden on that page. Long scrolling captures use `.device.tall` — a
correct-ratio frame whose contents scroll — because a 1:5 image stretches the
frame until it stops reading as a phone.

**Hero.** `index.html` picks a frame set once at load: `frames-1152/` when
`innerWidth <= 600`, else `frames/`, and `FRAME_W` follows. **On a big screen
the shut chest is sharp** (owner's asking, 2026-11-14, "main chest is bit
blurry", on a 2560×1440 monitor where the 1600 frames were stretched ~1.4–1.6×):
where `BIG_Q` matches (the canvas wants more than ~1800 device px: CSS width ×
pixel ratio), frame 0 is `art/hero/shut-hires.avif`, f000 cut at 2560×1444, and
the canvas may be up to 2560 wide (`sizeCanvas()`); the other 35 stay at 1600,
and from the last frame on the push-in draws the 3832 still as before. Its
`<link rel=preload>` takes `BIG_Q` as its media, and the `frames/` f000 preload
the negation (Media Queries 4 `not (… or …)`), so neither downloads twice; keep
the three in step. A whole 2560 set was tried first and came off: each new
frame's upload dropped a frame or two through the opening (~7 a pass at
2560×1440 against none with the 1600 set); with only frame 0 at 2560, measured
0 over 25ms at 1200px/s. It was cut on the Windows laptop with ffmpeg-static
and sharp from npm (not in the project): BT.709, black point 6 and power 1.04,
which is what the live 1600 frames measure as (the 8/1.05 below, applied to
ffmpeg's decode, came out ~2 levels darker than they are). **Re-cut on
2026-11-11 from the owner's new video** (`art/hero/_source/chest-animation-v2.mp4`,
3832×2164, 6.04s at 24fps; the same painted chest, its colours calmer): the
36 frames are video frames 36–144 evenly spaced (it holds still until ~45,
then the front board drops until the end), `frames/` now **1600×903** (it was
2304×1300: the canvas is about that wide on a laptop, and drawing the 2304
frames cost the scroll its frames), `frames-1152/` 1152×650, `open-hires.avif`
the last frame at full size, `poster.jpg` the first. All untiled AVIF, so
Firefox and Zen decode the sharp cut now; the old `frames/` and still were
tiled (grid) AVIFs, which they reject (found 2026-10-30: every frame fell to
the poster and the chest never opened). `decodeFrame()` still switches the
rest to `frames-1152/` if a desktop frame won't decode. The latch (`HASP`) and
the push-in's target (`TX`/`TY`) still fit the new frames. How they were cut:
Chrome pulled the frames from the video as PNG (no ffmpeg or Python on the
Windows laptop), and `sharp` encoded them after a darkening grade (owner's
asking the same day: the new chest "looks so pale and so exposed"; its
shadows sat at 57 of 255, milky): black point 8 and the mids taken down by
a power of 1.05, the same curve on R, G and B, baked into every frame, the
still and the poster, so it costs nothing to draw. Only a touch: black point
24 and a power of 1.16 went out first and was "tooooo dark, I just wanted
slightly tiny bit dark" (it turned the open interior and the dropped board
near black); don't go back past this unasked. Then AVIF quality 45, effort 6, 4:2:0
(the still at quality 62, 4:4:4: the push-in crops it up to 2.4×). Frames go through
`img.decode()`; don't switch to `createImageBitmap`, which has no AVIF decoder
in every engine and fails silently. `decode()` does not resolve in a hidden
tab, so a background tab's loader waits until it is shown — known. Dev HUD
only at `index.html?hud`. `README.md` covers the hero in depth.

## art/

- `art/hero/` — landing-page chest animation: `frames/` (36 AVIF, 1600×903,
  ~3.9MB), `frames-1152/` (36 AVIF, 1152×650, ~2.5MB), `poster.jpg` (stands in
  if f000 won't decode, 1600×903), `open-hires.avif` (3832×2164, 280KB), `shut-hires.avif` (f000 at 2560×1444, 294KB, big screens only). **Served**, ~7.3MB (its `_source/` holds the painting's crops,
  `chest-animation-v2.mp4`, the video the frames are cut from since 2026-11-11, and
  `chest.m4a`, the opening sound, unused since the sound toggle came off)
- `art/site/` — `cloud-bg.jpg`, `frieze.webp`, `khadag.webp`,
  `shagai/shagai-1…4.webp` (the four шагай a click tosses, cut out of the owner's sheet
  `_source/shagai/shagai-sheet.jpg` by flooding its paper and shadows from the edges up to each piece's closed
  tan outline, 96px tall), and `cloud-gold.webp`
  (the landing's transition stripes and timeline ground, 1600px lossless,
  149KB). **Served**, ~380KB
- `art/about/` — `gerege.webp`, `hee.svg`. **Served**, ~136KB
- `art/_archive/how-i-work/<object>/` (was `art/how-i-work/`; archived, unserved, since the section came off on 2026-11-15) — the frames the landing's How I Work played, 302 since 2026-09-30 (the draft
  `how-i-work-3d.html` that used all 992 is gone, and with it every frame the landing doesn't draw: pail-milk 48,
  pour 65, khokhuur 37, khokhuur-buluur 37, pull 65, khokhuur-rest 1, ayaga-khadag 48 + `hi/f000`; ~11MB). What follows
  describes the full sets as they were cut; the tools are in `.claude/scroll-rig/video/`. Originally turntable frames for `how-i-work-3d.html`:
  one even 360° turn as transparent WebP, `f000.webp`…, built in a template
  literal (`F.dir + 'f' + pad + '.webp'`). `pail-milk/` is step 1 now: 144
  frames 478×600 + `hi/` f000 1010×1268 (~6.2MB), from
  `art/how-i-work/_source/step 1 milk.mp4`, whose first frame is the pour's.
  Cut by `extract1n.html`/`export1n.py` with the pour's key (plus small shine
  specks shut inside, the rivets, kept solid); timed by the staves' texture
  (`plan1n.py`); held on the body, since a round tub's outline is centred on
  its axis (it wandered ±20px and 24px up and down). The box runs from the
  rope standing up mid-turn to the base, so `H` is 2.19 and the pail keeps
  its size; the pour's `from` is that box in the video.
  `pour/` is the step 1→2 pour: 193 frames, 648×720 (~7.3MB, q .80), every
  frame of `art/how-i-work/_source/step 1-2 pour.mp4` cropped to x 80–1376,
  cut by `extractp.html`/`exportp.py`: keyed off the white, plus the milk by
  its warmth (ivory's blue dips below its red and green; paper's never does),
  the milk's white core by closing that mask, and near-white milk shut inside
  the pail by an edge flood that keeps enclosed patches only if they are warm
  (the paper under the rope's arc is not). The floor's shadow under the lifting pail is keyed out in its first 35 frames (grey below each column's lowest coloured pixel), since the card keeps its own blob. The frame's edges fade, 40px where
  the objects stand at rest and 240px while the camera moves and they cross
  them. `pull/` is the step 3→4 pull: 193
  frames, 563×966 (~7.5MB), every frame of `art/how-i-work/_source/step 3-4
  pull.mp4`, box x 60–1400, y −860–1440: the pole's top, cut off by the
  video's first frame, is drawn back in above it (`extractpull.html`, step 3's
  method with a length per frame from `planpull.json`: step 3's 328 rows while
  the sack turns, up to 839 as the head comes out of the neck, back to 0 by the
  time the pole's own top comes into the frame). `khokhuur-rest/` is step 4's
  still: the pull's last frame, 587×600 + `hi/` 1330×1360. The start and end
  frames made for regenerating it with room above are
  `art/how-i-work/_source/step 3-4 start.png` / `end.png`. The old pail (below) is archived, unserved, in
  `art/how-i-work/_source/archive/pail-v1-frames/`. It was step 1: 144 frames,
  458×600, ~5.0MB, plus `pail/hi/`: 13 sharp 916×1200 frames (~1.4MB) for
  the angles it can rest at (frames 134–143, 0–2), cut from a Kling video and sharpened inside the silhouette only (unsharp mask .85/1.15px on `hi/`, .6/.8px on the turning frames; `extract.html` `render(…, amount, radius)`) (the video turned 1.5 times; the
  clean turn is source frames 0–110 + 150–192, retimed to an even 2.5° by
  the ears' spread). `khokhuur/` is step 2: 144 frames 607×600 (~5.6MB) + `hi/`
  13 at 1214×1200 (~2.1MB, frames 142–143, 0–10: it rests on the left), one clean
  turn retimed by the crossbar's length. `khokhuur-buluur/` is step 3: 144 frames
  497×600 (~3.9MB) + `hi/` 13 at 994×1200 (~1.3MB, frames 134–143, 0–2). Its
  video cut the pole off at the top edge, so `extract3.html` draws the missing
  top on every frame: 328px added above the frame, the pole's axis carried on
  at its measured slope, its cross-section averaged along rows 1–80 plus a
  little mirrored detail, and a rounded end. The turntable plate under it is
  keyed out as neutral grey below the lowest leather in each column. Steps 2
  and 3 are cut on a fixed turn axis (x 710 and 722 of 1440): step 3's plate
  shows the camera never moves, and the sack's own silhouette swings ±50px as
  it turns, so a centre of mass or base centre adds a sideways wobble. Both
  crops end at source row 1434, so their sacks share a scale. Turntables load
  in step order, each after the previous one's rest frames. `ayaga-khadag/` is
  step 6: 144 frames 988×540 (~4.2MB) + `hi/` f000 at 1746×954 (~120KB: it
  rests straight on, see `face`), cut by `extract6.html`. Its
  video's bowl sits off the turntable's centre and orbits ±70px, so each frame
  is held on the bowl itself (its rim's centre, widest row and width, smoothed)
  rather than a fixed axis. The turn is timed from the bowl's own texture
  (the front wall and wood band tracked frame to frame, less the bowl's
  travel): the video eases in and out, near still for its first and last
  half second. The turntable plate stays put in the frame, so it is keyed out
  inside its fixed ellipse wherever a pixel is neither bowl (a measured
  profile) nor хадаг blue (saturation); background is only what the paper
  reaches from the frame edge, so sheen and creases shut inside the хадаг
  stay; the near-white airag is held solid inside the rim, and along the rim
  only paper-white counts as paper. Where the fringe ran off the frame edge
  (about 8–69°, 173–214° and at 250° of the turn) it fades out. Its video was photographic next to
  the set's clean renders ("too realistic", the owner), so every frame then
  goes through `stylize6.js` (in the rig's `video/`, `export6.py stylize6.js`):
  in OKLab, an edge-preserving smoothing that flattens the tarnish and the
  silk's weave into satin, and a calmer, deeper blue at the set's saturation;
  alpha untouched, fixed parameters so the turn doesn't shimmer. The padded
  still it was made from is `art/how-i-work/_source/step 6 still.png`. Originals in
  `art/how-i-work/_source/`. **Served**
- `art/<case>/` — one folder per case study, straight under `art/` since 2026-09-30
  (it was `art/work/<case>/`): `netpay/`, `voice/`, `ohayofx/`, `hub/`. Design-system
  sheets live in `netpay/system/` and `voice/system/`. Filenames carry no case
  prefix — the folder is the prefix (`art/netpay/cover.jpg`). **Served**, ~16MB
- `_source/` inside each folder (`art/<project>/_source/`, `fonts/gip/_source/`) —
  that project's originals, exports, screen recordings and the rasters the WebPs
  replaced, sorted there on 2026-09-30 at the owner's asking ("netpay folder only
  netpay"); until then they were all in one `art/_source/`, sorted by case with a
  mixed `misc/`. NetPay's holds its old `misc/` things too (QA sheets under `qa/`, the
  loan, wallet and trust-fund flows and animations, the phone mockups), and
  `netpay-design-system/`. Tracked in git since that day (the owner's asking: the
  repo is how they move laptops), **never deployed** (`.vercelignore`: `_source/`).
  `art/netpay/_source/Netpay-mockup.png` (16000×12000, 130MB) is over GitHub's
  100MB limit, so it stays on disk only (gitignored) and its lossless WebP beside it,
  proven identical pixel for pixel, is the tracked copy. ~700MB in all.
- `art/_archive/` — originals of projects taken off the site (`smileline/`,
  `playground/`, and an old `misc/ai.html`). Tracked, never deployed.

Sizes are `du -sh`. Before moving anything in `art/`, grep the HTML, CSS and JS
for the path. Every served file is referenced and every reference resolves:
192 distinct paths (187 under `art/`, 5 under `fonts/`) for 192 files (the newest: `art/hero/shut-hires.avif`, 2026-11-14; before it the four шагай; How I Work's still and its 302 frames went to `art/_archive/` on 2026-11-15). SmileLine was taken off the site on 2026-09-27; its page and art are kept in `art/_archive/smileline/`. There
are no orphans, so a file that nothing references is a bug, not spare stock.

Count with a script, not a grep for `src=`/`url(`, which misses two things:
`index.html` builds its frame paths in a template literal
(`art/hero/${SET}/f${pad(i)}.avif`, both sets). Include `srcset` candidates, and skip
`.DS_Store` and paths that only appear in comments.

## Caching

- `serve.py` sends `Cache-Control: no-cache`: a plain reload shows edits,
  unchanged files come back 304, Back is instant. It has no Range support, so
  Safari may refuse the mp4s locally — judge video on a Vercel preview.
- `vercel.json`: `art/hero/*` is `public, max-age=31536000, immutable`, which
  is safe only because every hero URL carries `?v`. Other `art/*` and `fonts/*`
  get `public, max-age=86400, stale-while-revalidate=604800`, so a file
  replaced in place can stay stale for returning visitors for a day, and for
  one more visit in the week after while it revalidates. HTML, CSS and JS keep
  Vercel's default revalidation.
- `.vercelignore` keeps `CLAUDE.md`, `README.md`, `serve.py`, `.claude/`,
  every `_source/`, `art/_archive/`, `*.log` and `.DS_Store` out of the deploy. `outputDirectory`
  is `.`, so anything not listed there ships as a public URL.
- When a CSS or JS file changes, bump its `?v=` to the same new number on every
  page that links it. Check with
  `grep -ho '[a-z-]*\.\(css\|js\)?v=[0-9]*' *.html | sort | uniq -c` — one
  line per file means they agree.
- `ASSET_V` in `index.html` is the `?v` on the frames, poster and open-hires.
  Bump it together with the `?v` on both f000 `<link rel=preload>` lines in
  `<head>` (one per set, split by media query), or f000 downloads twice.
  (`chest.m4a`, which carried its own `?v`, is no longer served.)

## Data

Outcome figures on NetPay and Voice come from
`~/Downloads/NetPay v1 vs v2 Voice Engagement Sept 18 (1).xlsx`. Two traps:

- The Voice funnel in the workbook mixes sources. `voice_activity_log` starts
  2025-12-02; the quiz table covers 2025-10-27 → 2025-12-21. Counts from the
  two cannot be chained into one funnel, and the page says so. On Voice's
  chart book the quiz is its own sheet with its own caption for that reason.
- Voice's 6 138 is people who opened the section, distinct over the 13 weeks
  (from the workbook's summary sheet). The weekly counts sum to 6 755 because
  people return; never add them up as a total.
- NetPay's four-month windows are 2025-05…08 against 2025-10…2026-01. Derived
  rates are recomputed from the raw columns (MAU, total minutes, active
  user-days), never from the workbook's own ratio columns.

Recompute from raw columns and re-verify contrast after changing a panel fill —
the faintest ink sits near the 4.5:1 line at 10.5px.
