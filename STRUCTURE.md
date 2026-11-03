# Site structure — the desk library

This site is a library, not a page. It grows by adding folders under the
convention below. Nothing here ever gets restructured to make room for a
new slate or a new sport: if a change seems to require moving an existing
path, the change is wrong.

## Layout

```
/                       Library home: the sports, the convention, the rules
/styles.css             The one stylesheet. No build step, no external assets
/nhl/                   Sport index: slates newest first, standing pages
/nhl/history.html       Standing reference for the sport (not slate-bound)
/nhl/2026-11-03/        One folder per slate, named by date (YYYY-MM-DD)
/nhl/2026-11-03/index.html        Slate index: the bar, slate state, game list
/nhl/2026-11-03/field-notes.html  The slate's news and sentiment sweeps
/nhl/2026-11-03/ana-van.html      One page per game
/nba/                   Opens with its first slate, same convention
/nfl/                   Opens with its first slate, same convention
```

Paths are sport / date / page. A game's filename is the two team codes,
away team first, lowercase, hyphenated (`ana-van.html`, `det-tb.html`).
Team codes are the pool's three-letter codes.

## What a slate folder contains

- `index.html` — the slate index. Carries the slate's measured bar (win
  expectation, top-1% cut, top-0.1% cut, min-cash for the desk's main
  contest), each figure labelled with its sample size and linked to the
  sport's standing history page; a slate-state banner for anything that
  moved after the trees were built; the game list with one factual line
  per game and a status per game (tree building / tree ready); and the
  entries the desk holds on the slate, if any.
- `field-notes.html` — the slate's news and sentiment record. News first
  (injuries, starters, line changes; sourced and tiered), sentiment
  second, behind the printed firewall: sentiment is an
  ownership-expectation read only and never touches a probability, a
  projection or a capture rate. Later sweeps append to the page; earlier
  sweep text is not edited.
- One page per game, built from that game's tree file in the desk's
  build folder. A game gets a page when its tree file exists, and not
  before. Until then the slate index lists the matchup as "tree
  building" with no link and no invented content.

## Game page anatomy

Every game page carries, in order:

1. Header: a full-sentence takeaway headline; the measure in the
   subtitle (puck drop, total, implied goals, win probability, method).
2. Level 1, the game: goal distributions for both teams and the ten
   scripts with probabilities as bars, expected goals per script, and
   what each script pays. Lenses (overlapping views) follow, labelled
   as lenses, never added to the scripts.
3. Level 2, capture: who holds the points under the scripts, measured
   from shared goals in the play-by-play — assist networks, unit
   capture on the goals the unit exists for, unit score distributions,
   and the key players' chance of 20+ priced from points alone and from
   all scoring sources. The method's blind spots are stated on the page.
4. Goalies: full distributions with P(20+), from inside the same
   simulation. A correction banner sits on this section whenever the
   crease moved after the tree was built; superseded distributions are
   labelled superseded, never deleted and never presented as live.
5. Scoring audit: the sport's verified scoring table, what does not
   score, and the game-specific notes (hidden-points floors, bonus
   holders). Nothing enters a tree that is not on the verified list.
6. Level 3, the leaves: expandable sections, each with its tier (core,
   secondary, convex, or dead/reclassified with the reason), its priced
   probability, its construction with salaries, and its share of the
   slate's entries. A convex leaf is never built naked: its remaining
   slots are core assets, and the page says so.
7. Trust limits and the bar: how far the page's numbers can be trusted
   (backtest verdict, tolerances, haircuts, softest inputs), and what
   the game must contribute toward the slate's measured bar, linked to
   the sport's history page.

## Adding a slate

1. Create `/<sport>/<YYYY-MM-DD>/`.
2. Write the slate `index.html` from the bar for that slate's game
   count, taken from the sport's history page or a fresh history pull.
3. Add `field-notes.html` with the first sweep; append later sweeps.
4. Build each game page as its tree file lands; flip the slate index
   line from "tree building" to a link when the page exists.
5. Add the slate line to the sport index, newest first, with the bar
   figures on the line.
6. Push. No existing file moves, and no link changes.

## Adding a sport

Create `/<sport>/index.html` with the library home's sport row flipped
from "opens with its first slate" to a link, and build the sport's
standing history page before or with its first slate: a slate's bar is
never published without the measured history behind it.

## Design rules (the approved presentation)

Warm light ground (#F7F5F0), ink text, serif display headings (Fraunces,
Georgia fallback), one accent (#C8371F), full-sentence takeaway
headlines, the measure in the subtitle, direct labels on the data,
probabilities as bars, leaves as expandable sections. No card soup, no
gradients, no emoji, no external assets. Annotation reads like
journalism: every number labelled measured, market or modelled, with
its sample size where it has one.
