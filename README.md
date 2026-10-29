# Colorado Trail Partnership Atlas

A single-file, no-dependency HTML tool that compares Front Range Colorado towns on whether they partner with a nonprofit trail-advocacy organization (COMBA, Medicine Wheel Trail Advocates, Boulder Mountainbike Alliance, etc.) versus building trails entirely in-house. Built as an advocacy resource for Castle Rock trail advocacy — the core argument is that partnership is the regional norm, not an ask that singles Castle Rock out.

**Live file:** `index.html` — a single HTML file with inline CSS and JS. No build step, no npm install, no external requests except the outbound links in the write-up and footer. Drop it straight into a GitHub Pages repo.

---

## ⚠️ This data will go stale — treat it as a snapshot, not a source of truth

This is the most important thing in this README. The original survey was compiled from web searches and public agency pages on **July 7, 2026**, with a sourcing pass adding primary-source links for every row on **August 2, 2026**. A review on **October 28, 2026** added the population and per-capita columns, refreshed the Conifer and Centennial rows, and replaced a dead Black Hawk link. Nearly every field in it is the kind of fact that changes:

- **Trail mileage changes constantly.** Jeffco Open Space, Colorado Springs Parks, and city departments build new trail, close trail for restoration, and reroute existing trail every season. Treat mileage figures as estimates, not counts — see [Data & Confidence](#data--confidence) below.
- **Partnership status can change.** A town that says "no" to a nonprofit today could sign an MOU next year — and vice versa, a partnership could lapse. This tool is exactly the kind of resource that gets stale-and-wrong quietly, which is worse than being visibly outdated.
- **Org rosters shift.** COMTB's member list, COMBA's active project list, and even the mailing addresses on Jeffco trailheads (see the Littleton/Deer Creek Canyon note in the tool) can all move.
- **New towns should get added.** This survey covers 23 municipalities across 8 counties. It is not exhaustive — it's a working sample built to make an argument, not a census.
- **In-progress projects need the most frequent recheck.** Conifer High School's campus trail system (added August 2026) was fundraising for a second phase, with a Jefferson County Trails Partnership Grant match if the goal was reached by Sept. 1, 2026. That deadline has passed and the outcome is unconfirmed (the GoFundMe's last visible update was dated 8/20 and said the campaign was about $2,750 short) — confirm with COMBA before citing Phase 2 or a 6-mile total.
- **Links break.** The City of Black Hawk reorganized its website in 2026 and the Maryland Mountain page this tool used to link now returns a 404, so that row points to Boulder Mountainbike Alliance's May 2021 opening report until the city's new page is found. A quick link check once or twice a year catches this; several city sites (Castle Rock, Centennial, Englewood, Arvada, Commerce City, Idaho Springs, Highlands Ranch) answer automated checkers with a 403 even though they load fine in a browser, so test those by clicking them.

**Recommended cadence:** re-verify the partnership-status column at least once a year, and before any formal presentation (Town Council, grant application, etc.) re-check the specific towns you're citing directly. Mileage figures are lower-priority to refresh unless you're citing an exact number out loud — though it's worth spot-checking any row whose source link is more than a year old.

---

## What's in the tool

- **Collapsible summary chart** — at the top, under the headline numbers: every town with a usable population figure, ranked by miles of singletrack per 10,000 residents. Click or press Enter on its heading to hide or show it (it starts open). Blue bars are towns that partner with a trail-advocacy nonprofit, orange bars are towns that don't, and Castle Rock's row is highlighted. A faded bar with a † means the mileage counts nearby Jeffco parks, so the ratio is overstated. Towns too small for a meaningful ratio, and towns with no population figure, are listed under the chart as "Not shown". Hovering, tab-focusing (arrow keys move between rows), or tapping a bar shows the arithmetic behind it. It is built from `DATA`, so it needs no edits when a town is added. See [The summary chart](#the-summary-chart) below.
- **Sortable/filterable data table** — 23 towns, 8 counties, click any column header to sort, filter chips for partnership status and county, live search, and a Compact/Full detail toggle. On a phone, Full detail is a stack of cards and Compact is a dense one-row-per-town table you can sort by tapping its headers.
- **Population and miles-per-10,000-residents columns** — each town's population and its singletrack mileage divided by it, sortable like the rest. See [Population and the per-capita column](#population-and-the-per-capita-column) for what the number can and can't say.
- **Row footnotes** — any row can carry a numbered footnote (a small marker beside its miles and a matching line under the table). Castle Rock uses one to say its 40 miles excludes the hiking-only Lost Canyon Ranch Open Space, and Colorado Springs uses one to say that the new trail Singletracks reported in January 2025 (more than 70 miles planned, plus a possible lift-served bike park) is not added to its 100 miles. Footnotes follow the filters, so a filtered table never shows a note for a row that isn't on screen.
- **Search and social-preview tags, and a license footer** — the page carries a description, Open Graph and Twitter-card tags (matching the PMR wrapper page), a phone-browser `theme-color` that follows the active theme, and the PMR license line at the bottom. See [License](#license).
- **Per-row source citations** — most rows carry a direct link to the town's own parks/trails page or the news article the entry is based on, shown as a small "Source ↗" link under the town's note. Rows without one just don't show the link.
- **Three color themes** (Blue Hour / Alpenglow / Meridian), consistent with the rest of the PMR tool suite.
- **Mobile-first table** — below 680px the table becomes stacked cards with a colored left edge (green = partner, red = no partner) instead of a horizontally-scrolling grid. The **Compact** toggle on a phone switches to a real table instead: one row per town showing partner?, miles, per-10k and confidence (county sits under the town name, and the note, source link, nonprofit and population columns are left out), with short column headers you can tap to sort. It is about 85% shorter than the card view (roughly 1,350px against 9,000px for all 23 towns). Before October 29, 2026 it only hid a few lines per card and was just 15% shorter, so it looked almost the same.
- **Write-up section** making the "why partner" case: grant eligibility, volunteer labor, trail design/sustainability, and political constituency — anchored with real numbers from COMBA, Medicine Wheel, Boulder Mountainbike Alliance, CAMBA (Wisconsin), and Northwest Arkansas/Bentonville, plus a pointer to the [Trail Advocacy Atlas](https://www.postmillenniumrenaissance.com/trail-advocacy-atlas/) for the national picture (440+ nonprofit trail organizations catalogued).
- **COMTB callout** — links to the Colorado Mountain Bike Coalition and its member directory, framing local partnerships as access to a statewide network, not just a local volunteer crew.

---

## Data & Confidence

Every row carries a `conf` value (1–3) rendered as a Low/Medium/High badge:

| Confidence     | Meaning                                                                                                                                          |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **High (3)**   | Partnership status confirmed directly on the organization's own project page or a public agency record.                                          |
| **Medium (2)** | Reasonably well-sourced but mileage is an estimate, spans multiple source disagreements, or the town/park relationship has a caveat (see below). |
| **Low (1)**    | Thin sourcing — treat as a placeholder to verify, not a citable fact.                                                                            |

**What the mileage column counts:** dirt singletrack that is open to mountain bikes, and nothing else. Many towns publish one trail-mileage number that mixes paved paths (similar to sidewalks) with dirt singletrack, so a town's headline figure usually overstates what this column should show. The table's mileage caveat says this in the author's own words. When a source gives only an all-surface total, don't copy it into `miles`: keep the singletrack estimate and, if the total is worth showing, put it in the note instead (for example, Lakewood's city page reports 240 miles of trails of all surfaces, which is a different measure from its singletrack).

**The recurring caveat:** several entries (Littleton, Morrison, Evergreen, Golden) reference trail mileage in **Jeffco Open Space parks** near those towns rather than trails the towns themselves own or fund. This is noted in each row's description. It doesn't undercut the argument — the point is what a partnered community has *access to* — but it's exactly the kind of distinction an opposing department head will reach for, so it's better surfaced here than sprung on you in a meeting.

**Highlands Ranch is marked "No."** HRCA (Highlands Ranch Community Association) manages Backcountry Wilderness Area trails, but HRCA is a homeowners association structured as a nonprofit — not a mountain-bike trail-advocacy organization like the COMTB member groups. This distinction is called out directly in the tool's write-up.

**Don't confuse the City of Centennial with Centennial Cone Park.** The Centennial row is the City of Centennial in Arapahoe County (suburban south metro, mostly paved greenways). Centennial Cone Park is a different place entirely: a large Jeffco Open Space park whose trailheads are all Golden, CO 80403 addresses, in Jefferson County. Its mileage does not belong on the Centennial row. Jeffco's own page describes "a 12-mile trail loop" (a Jeffco hunting-safety map lists the loop at 12.1 mi and Singletracks at about 13 mi); a "16.2 trail miles" figure was not found on the Jeffco page or in any search result when this was checked in October 2026. If Centennial Cone is ever counted, it would belong with the Golden-area Jeffco parks in the Golden row, with that same Jeffco caveat.

**Source links track roughly with confidence.** When a row's confidence was raised (e.g. Parker moved from Medium to High in August 2026), it's because a primary source — usually the town's own map or page — was found and linked at the same time. If you add a source for a row, it's worth reconsidering whether the confidence badge should move too.

---

## Population and the per-capita column

**The formula:** singletrack miles ÷ population × 10,000, shown as "Mi. per 10k residents". The unit is a setting (`PER_CAPITA_UNIT` / `PER_CAPITA_LABEL` near the top of the logic), not typed into the page.

**Where population comes from** (added October 28, 2026):
- **Incorporated places (20 of 23 rows):** U.S. Census Bureau city and town population estimates, **Vintage 2025, July 1, 2025** — the `sub-est2025.csv` file in the Census "Cities and Towns Totals 2020–2025" release (published May 2026).
- **Highlands Ranch and Evergreen:** unincorporated census-designated places, which the Census does not estimate annually, so they carry the **2020 Census count** (PL 94-171 redistricting file). The row sets `popYear:2020` and the table shows a small "2020" beside the number.
- **Conifer:** blank. The Census no longer defines a Conifer place, and a ZIP-code or school-district population would be a different geography. The table shows "—" rather than a substitute.

**What the ratio cannot say — read before quoting it:**
- It divides by the town's own residents, so it ignores riders who drive in. Destination trail towns look better than they "feel" per resident, and bedroom suburbs the reverse.
- It is only as good as the mileage column, which the page already calls the softest data in the tool.
- **† rows** (Littleton, Golden, Morrison, Evergreen) count Jeffco Open Space parks near the town, not trails the town owns, so the ratio is overstated. The same four rows are the "recurring caveat" above.
- **n/m rows** (Morrison, Idaho Springs, Black Hawk) are under `MIN_POP_FOR_RATIO` (2,500 residents, the Census Bureau's urban/rural line). A town of 120 hosting a regional trail system divides to roughly 800 miles per 10,000 residents, which says nothing. Set the constant to 0 to show every ratio anyway.
- Estimates for fast-growing towns move quickly. A 2020 count would flatter Castle Rock and Parker (both grew 13–15% since); that is why the incorporated places use the newest vintage.

**To refresh it:** download the newest `sub-est20XX.csv` from the Census Bureau's population-estimates datasets, find each town's row (state `08`, summary level `162`, name like `Castle Rock town`), copy the latest `POPESTIMATE` column into the row's `pop`, and update `POP_YEAR` to match. The Census API now asks for a key; the flat CSV does not. (The October 2026 numbers were pulled and cross-checked by script, not typed.)

---

## The summary chart

**What it plots:** the same ratio as the table's "Mi. per 10k residents" column (miles ÷ population × 10,000), for every town that has one, ranked high to low. Which towns appear, their order, the axis, and the "Not shown" line under the chart are all worked out from `DATA` each time the page loads, so adding or editing a town needs no chart change.

**Reading it:**
- The scale is linear and starts at zero, on purpose. Evergreen and Golden dwarf the plains suburbs (0.07 to 0.31 per 10,000), and that spread is real. A log scale would make the suburbs look comparable to the destination towns, which would mislead. The faded † bars are the honest explanation for the two biggest bars: their mileage is in nearby Jeffco parks.
- Blue bars are partner towns and orange bars are towns with no trail-advocacy partner. These colors are deliberately not the green/red of the table's Yes/No badges: a red/green pair is the classic color-blind trap, and blue/orange is not.
- Color is never the only signal. A filled dot marks a partner and a ring marks a non-partner, the value is printed at the tip of every bar, and the table below has every number.

**Colors were validated, not eyeballed.** Each theme's pair was run through the dataviz skill's palette checker against that theme's actual panel color: color-blind separation ΔE 24.7 or better (the target is 8), normal-vision separation above 31, and contrast over 3:1. Blue Hour and Meridian use `#2a78d6` / `#eb6834`; Alpenglow uses its dark-surface steps `#3987e5` / `#d95926`; print uses a darker blue (`#1c5cab`) so the two bars also differ as greys on a black-and-white printout.

**Tooltips enhance, they never gate.** Hover, keyboard focus (Tab into the list, then the up and down arrow keys; Escape closes) or a tap shows the arithmetic ("48 mi ÷ 20,390 residents"). Everything a tooltip says is already on the row or in the table.

**Collapsing** uses a native `<details>` element, so it works by keyboard and screen reader with no script. It starts open; to start it collapsed, remove `open` from `<details class="chart-panel" id="chartPanel">`.

**Printing:** an open chart prints on page 1 under the headline numbers, a collapsed one stays collapsed. It is sized to fit in the space left on page 1. If you add content above it, check that it still fits: when it doesn't, the chart is kept whole and moves to page 2, which leaves page 1 half empty and adds a page.

---

## How to update the data yourself

You don't need to touch any HTML or CSS to update a town's numbers. Open `index.html` in any text editor and search for `const DATA = [` near the top of the `<script>` block — it looks like this, one object per town:

```js
{ town:"Golden", county:"Jefferson", status:"yes", org:"COMBA", miles:48, conf:2, pop:20390, nearby:true, source:"https://www.cityofgolden.gov/community/parks_trails/index.php", note:"..." },
```

- `status` is `"yes"` or `"no"`
- `miles` is a plain number
- `conf` is `3` (High), `2` (Medium), or `1` (Low)
- `pop` (optional) — residents of the town itself, a plain number with no commas. Leave it off if there is no Census place for the town; the page then shows "—". See [Population and the per-capita column](#population-and-the-per-capita-column) for which Census figure to use.
- `popYear` (optional) — only set it when the row's `pop` is not the default `POP_YEAR` vintage (for example `2020` for an unincorporated place). It adds a small year tag next to the number.
- `nearby` (optional) — `true` when the miles are in nearby Jeffco Open Space parks rather than trails the town owns. It adds a † to the per-capita figure and the town to the legend under the table.
- `foot` (optional) — a footnote, as text that may include a link. It puts a numbered marker beside the row's miles and a matching line under the table. Numbers follow the order of rows in `DATA`, so a marker keeps its number when the table is sorted or filtered. Use it for a fact about *what the mileage includes or excludes* that is too long for the row's note.
- `note` is the short line that appears under the town name — keep it to one or two sentences
- `source` (optional) — a URL string. If present, a small "Source ↗" link appears under the note, in both the desktop table and the mobile card view. Leave it off if you don't have a good primary source yet.
- `foothills` (optional, only meaningful on Douglas County rows) — `true` or `false`. It is a record of which Douglas County towns sit on foothills terrain (Castle Rock, Highlands Ranch) versus plains/paved-trail terrain (Parker). **Nothing on the page is computed from it any more** (a "go it alone" number in the top strip used it until October 2026; that number has since been removed). The write-up's Castle Rock section still makes the foothills distinction in typed prose. You don't need to set this on a new town.

**To add a new town:** copy an existing line, change every field, and add a comma. Everything else updates itself automatically — no other edits needed:
- The table, filters, sort, and mobile card view
- The **county filter chips** — these are generated from whatever counties actually appear in `DATA`, so a brand-new county gets a working filter chip with zero HTML editing
- The **thesis-strip numbers** at the top of the page (town count, county count, and the COMTB member count)

**To add a new "why partner" case study** (the CAMBA / NWA Trailblazers / COMBA & Jeffco cards further down the page), search for `const CASE_STUDIES = [`, just below `DATA`. Same pattern — copy an object, change `tag`, `name`, `loc`, `stat`, `statLbl`, and `body`, add a comma. The cards render themselves; no HTML editing needed.

**To add a new color theme**, search for `const THEMES = [`. It's a two-step process now:
1. Add a new `html[data-theme="yourkey"] { ... }` block up in the `<style>` section, copying the variable list from an existing theme (bluehour, alpenglow, or meridian).
2. Add one entry to the `THEMES` array with the same key and your theme's `--bg`/`--accent` hex values (used to draw the little swatch preview button).

The swatch button, its click handler, and the pressed/active state all generate themselves from that array — you don't need to add or edit any button markup.

If editing raw JavaScript isn't your thing, the fastest path is to paste the relevant section of this file into a Claude conversation along with whatever new information you've found (a news article, an org's project page, an updated Trailforks number) and ask for the update. That's exactly how this file has been built and revised throughout.

---

## Sources used to build the current version

**Organizational & regional:**
- Colorado Mountain Bike Coalition — [comtb.org](https://comtb.org) and its [member directory](https://comtb.org/colorado-trail-organizations/)
- COMBA — [comba.org](https://www.comba.org), especially the [trail systems page](https://www.comba.org/trail-systems) and project-status pages
- Medicine Wheel Trail Advocates — [medwheel.org](https://medwheel.org)
- Boulder Mountainbike Alliance — [bma-mtb.org](https://www.bma-mtb.org)
- CAMBA (Chequamegon Area Mountain Bike Association, WI) — [cambatrails.org](https://www.cambatrails.org)
- Walton Family Foundation / University of Arkansas economic impact studies on Northwest Arkansas trails
- Trailforks, COTREX, and individual city trail pages for mileage cross-checks
- U.S. Census Bureau — [city and town population estimates, Vintage 2025](https://www2.census.gov/programs-surveys/popest/datasets/2020-2025/cities/totals/sub-est2025.csv) and the [2020 Census redistricting (PL 94-171) file for Colorado](https://www2.census.gov/programs-surveys/decennial/2020/data/01-Redistricting_File--PL_94-171/Colorado/co2020.pl.zip), used for the population column
- Independent Sector — [value of volunteer time](https://independentsector.org/volunteer_time). The write-up uses the **2025 national figure, $36.14/hr** (released April 21, 2026, built on preliminary wage data and a larger fringe-benefit uplift than earlier years, so part of the jump from 2024's $34.79 is method, not wages). The Trail Advocacy Atlas's Why tab and the Trail Investment ROI Calculator still use $34.79 and must be changed together with each other.

**Town & county primary sources (linked per-row as of August 2026, updated October 2026):**
- Douglas County — [Castle Rock](https://www.crgov.com/1985/Open-Space-and-Trails) (the footnote on its mileage cites the Town's [Lost Canyon Ranch Open Space page](https://www.crgov.com/lostcanyonranch); the hiking-only rule was confirmed on the [Colorado Mountain Club listing](https://www.cmc.org/education-adventure/trips/routes-places/lost-canyon-ranch-open-space), which says "Trails are limited to hikers only" and bikes are "permitted only on roadways" — the Town's own page blocked automated checking), [Parker](https://www.parkerrec.com/301/PARKS-TRAILS), [Highlands Ranch / HRCA](https://hrcaonline.org/Recreation/Backcountry-Wilderness-Area/Trails)
- Jefferson County — [Jeffco Open Space: Deer Creek Canyon](https://www.jeffco.us/1208/Deer-Creek-Canyon-Park), [Crown Hill Park](https://www.jeffco.us/1207/Crown-Hill-Park); [Golden](https://www.cityofgolden.gov/community/parks_trails/index.php), [Lakewood / Singletracks](https://www.singletracks.com/mtb-trails/new-bike-optimized-beginner-flow-trail-opens-at-bear-creek-lake-park-near-denver-co/), [Morrison](https://www.morrisonco.us/130/Parks-Trails), [Evergreen](https://www.evergreenrecreation.com/trails), [Arvada](https://www.arvadaco.gov/508/Parks-Trails-and-Open-Space), [Conifer / CHS Today](https://chstoday.net/5669/news/new-proposed-trail-system-on-campus/)
- El Paso County — [Colorado Springs](https://coloradosprings.gov/parks-trails-open-space) (the footnote on its mileage cites [Singletracks, Jan. 29, 2025](https://www.singletracks.com/mtb-trails/colorado-springs-is-working-on-75-miles-of-new-mtb-trails-and-maybe-even-a-lift-served-bike-park/), a news report rather than a City document. A later [Gazette report, Jan. 12, 2026](https://gazette.com/2026/01/12/expanded-trails-future-destinations-among-this-years-plans-for-pikes-peak-region/) said Blodgett Open Space's 14 miles of new and improved trail were expected to finish around summer 2026 and that Fishers Canyon would not open to the public in 2026; status after that has not been checked), [Monument](https://townofmonument.org/277/Parks-and-Open-Space-Department)
- Adams County — [Thornton](https://www.thorntonco.gov/parks-recreation/parks-planning), [Brighton](https://www.brightonco.gov/254/Parks-Recreation), [Commerce City](https://www.c3gov.com/Government/Facilities/Sand-Creek-Regional-Greenway-Commerce-City-Wetlands-Park), [Westminster](https://www.westminsterco.gov/381/Open-Space-Trails)
- Arapahoe County — [Aurora](https://www.auroragov.org/things_to_do/parks__open_space___trails), [Centennial](https://www.centennialco.gov/Government/Departments/Parks-Trails-Open-Spaces) (plus [Arapahoe County Open Spaces: Dove Valley Regional Park](https://www.arapahoeco.gov/business_detail_T15_R81.php), linked inside the Centennial note; bike-park length from [MTB Project](https://www.mtbproject.com/trail/7071870/dove-valley-bike-park), a user-submitted listing), [Englewood](https://www.englewoodco.gov/parks-recreation-library-golf/play-englewood-recreation/parks)
- Boulder County — [Boulder OSMP](https://bouldercolorado.gov/government/departments/open-space-mountain-parks)
- Clear Creek County — [Idaho Springs / Virginia Canyon Mountain Park](https://www.idahospringsco.com/home-page/page/virginia-canyon-mountain-park-vcmp)
- Gilpin County — [Black Hawk / Maryland Mountain, via Boulder Mountainbike Alliance's May 2021 opening report](https://www.bouldermountainbike.org/maryland-mountain-grand-opening/). The City of Black Hawk's own page (`cityofblackhawk.org/things-do-black-hawk/page/maryland-mountain-quartz-valley-open-space-park-hiking-biking`) returned a 404 in October 2026 and should be re-linked once the city's new address is found.

---

## Roadmap / ideas not yet built

- Population growth next to the per-capita column. The Vintage 2025 Census file already carries the 2020 base and the 2025 estimate, so "population change since 2020" is a one-field addition per town and shows which towns' per-capita figures are falling fastest
- 5-year trail-mileage growth rate (isolates *capacity to expand*, which is the sharper version of the Castle Rock argument)
- Grant dollars secured via nonprofit partner, where publicly documented
- Annual volunteer trail-work hours by town/org
- A "delivery model" column (in-house / contractor / nonprofit / hybrid) instead of a strict yes/no, since the strongest systems combine all three
- Since every row now carries a source link, a "last verified" date per row would be a natural next addition — it'd make the annual reverification pass much easier to track

---

## For future edits — quick orientation to the code

If you're pasting this file into a new Claude conversation to make a change, here's the shape of it: town data lives in `DATA`, the national case-study cards live in `CASE_STUDIES`, and the color themes live in `THEMES` — all three are plain arrays near the top of the `<script>` block. Everything visible on the page (the table, the filters, the county chips, the case-study cards, the theme swatches, and the thesis-strip numbers) is generated from those three arrays at load time; none of it is hand-typed into the HTML. That means almost any data change — a new town, a new case study, a new theme, a new source link — is a one-line edit to an array, not a hunt through multiple sections of the file.

A few things in the file are **not** driven by `DATA` and are easy to let drift:
- **The `<head>` description and social-preview tags** deliberately match the PMR wrapper page at `postmillenniumrenaissance.com/trail-partnership-atlas/` (same description, title and the site-wide `og-image.jpg`), so a link to this file previews the same as a link to the branded page. If you change one, change the other. There is no `og:url`, so a preview uses whichever address was actually shared.
- **The numbers in the write-up prose** (for example the volunteer-hour value and the Trail Advocacy Atlas count) are typed text, not computed. Re-check them on each annual pass.
- **The settings above `END OF DATA`** (`POP_YEAR`, `PER_CAPITA_UNIT`, `PER_CAPITA_LABEL`, `MIN_POP_FOR_RATIO`, and the chart's `CHART_HIGHLIGHT_TOWN`, `CHART_MAX_TICK_INTERVALS`, `CHART_MIN_BAR_PCT`) feed the table, the chart, the legends and the column header, so change them there and nowhere else.
- **The chart's two series colors** (`--chart-partner`, `--chart-none`) live in each theme's CSS block and in the print block, not in JavaScript. Each pair was validated against that theme's panel color, so re-validate if you change one or add a theme. See [The summary chart](#the-summary-chart).
- **The short column labels** used by the phone compact view are the `.th-short` spans in the table header. If you rename a column, update its short label too; the long label (`.th-full`) is what the print header and sort description use.

---

## License

The page and this repository are licensed under the [PolyForm Noncommercial License 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0/), the same license as the Trail Advocacy Atlas (full text in `LICENSE`). Every edit and rebuild must keep: the `Required Notice:` line at the top of `LICENSE`; the `(c) / SPDX` comment right after the doctype in `index.html`; and the visible license line at the bottom of the page. Do not remove, reword or hide them. Third-party material keeps its own license and notices: the Census Bureau figures are public data, and the studies cited in the write-up remain the property of their authors. The copyright holder decides any change to the license.

---

## Project context

Built for **Post Millennium Renaissance MTB** — [postmillenniumrenaissance.com](https://www.postmillenniumrenaissance.com) — as part of ongoing trail advocacy work in Castle Rock, Colorado. No build tooling, no dependencies, single HTML file, deploys directly to GitHub Pages.

*Last substantive update: October 29, 2026 (added the collapsible summary chart, rebuilt the phone Compact view as a dense sortable table, removed the "partner with a nonprofit" and Douglas County "go it alone" counts from the top strip, and added a Colorado Springs footnote on the new trail Singletracks reported in January 2025). Last substantive data update: October 28, 2026 (23 towns, 8 counties — added population and per-capita columns, refreshed the Conifer and Centennial notes, replaced the dead Black Hawk link, updated the Trail Advocacy Atlas count to 440+, set the volunteer-hour value to Independent Sector's 2025 figure of $36.14, reworded Castle Rock's note to "no mountain-bike trail-advocacy nonprofit partner", added a footnote that its 40 miles excludes Lost Canyon Ranch, added the mileage-accuracy caveat, search and social-preview tags, and the license footer). Previous: August 2026 (added Conifer, refreshed Idaho Springs mileage, added source citations to every row). If you're reading this more than a few months later, assume at least a few mileage figures and possibly a partnership status or two have changed — reverify before citing anything in a formal setting.*
