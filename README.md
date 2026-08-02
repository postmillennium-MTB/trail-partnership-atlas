# Colorado Trail Partnership Atlas

A single-file, no-dependency HTML tool that compares Front Range Colorado towns on whether they partner with a nonprofit trail-advocacy organization (COMBA, Medicine Wheel Trail Advocates, Boulder Mountainbike Alliance, etc.) versus building trails entirely in-house. Built as an advocacy resource for Castle Rock trail advocacy — the core argument is that partnership is the regional norm, not an ask that singles Castle Rock out.

**Live file:** `index.html` — a single HTML file with inline CSS and JS. No build step, no npm install, no external requests except the outbound links in the write-up and footer. Drop it straight into a GitHub Pages repo.

---

## ⚠️ This data will go stale — treat it as a snapshot, not a source of truth

This is the most important thing in this README. The original survey was compiled from web searches and public agency pages on **July 7, 2026**, with a sourcing pass adding primary-source links for every row on **August 2, 2026**. Nearly every field in it is the kind of fact that changes:

- **Trail mileage changes constantly.** Jeffco Open Space, Colorado Springs Parks, and city departments build new trail, close trail for restoration, and reroute existing trail every season. Treat mileage figures as estimates, not counts — see [Data & Confidence](#data--confidence) below.
- **Partnership status can change.** A town that says "no" to a nonprofit today could sign an MOU next year — and vice versa, a partnership could lapse. This tool is exactly the kind of resource that gets stale-and-wrong quietly, which is worse than being visibly outdated.
- **Org rosters shift.** COMTB's member list, COMBA's active project list, and even the mailing addresses on Jeffco trailheads (see the Littleton/Deer Creek Canyon note in the tool) can all move.
- **New towns should get added.** This survey covers 23 municipalities across 8 counties. It is not exhaustive — it's a working sample built to make an argument, not a census.
- **In-progress projects need the most frequent recheck.** Conifer High School's campus trail system (added August 2026) is actively fundraising for a second phase as of this writing — check whether Phase 2 has closed before citing the 3-mile figure in anything formal.

**Recommended cadence:** re-verify the partnership-status column at least once a year, and before any formal presentation (Town Council, grant application, etc.) re-check the specific towns you're citing directly. Mileage figures are lower-priority to refresh unless you're citing an exact number out loud — though it's worth spot-checking any row whose source link is more than a year old.

---

## What's in the tool

- **Sortable/filterable data table** — 23 towns, 8 counties, click any column header to sort, filter chips for partnership status and county, live search, and a Compact/Full detail toggle for scanning quickly on a small screen.
- **Per-row source citations** — most rows carry a direct link to the town's own parks/trails page or the news article the entry is based on, shown as a small "Source ↗" link under the town's note. Rows without one just don't show the link.
- **Three color themes** (Sandstone / Alpenglow / Meridian), consistent with the rest of the PMR tool suite.
- **Mobile-first table** — below 680px the table becomes stacked cards with a colored left edge (green = partner, red = no partner) instead of a horizontally-scrolling grid.
- **Write-up section** making the "why partner" case: grant eligibility, volunteer labor, trail design/sustainability, and political constituency — anchored with real numbers from COMBA, Medicine Wheel, Boulder Mountainbike Alliance, CAMBA (Wisconsin), and Northwest Arkansas/Bentonville, plus a pointer to the [Trail Advocacy Atlas](https://www.postmillenniumrenaissance.com/trail-advocacy-atlas/) for the national picture (370+ nonprofit trail organizations).
- **COMTB callout** — links to the Colorado Mountain Bike Coalition and its member directory, framing local partnerships as access to a statewide network, not just a local volunteer crew.

---

## Data & Confidence

Every row carries a `conf` value (1–3) rendered as a Low/Medium/High badge:

| Confidence     | Meaning                                                                                                                                          |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **High (3)**   | Partnership status confirmed directly on the organization's own project page or a public agency record.                                          |
| **Medium (2)** | Reasonably well-sourced but mileage is an estimate, spans multiple source disagreements, or the town/park relationship has a caveat (see below). |
| **Low (1)**    | Thin sourcing — treat as a placeholder to verify, not a citable fact.                                                                            |

**The recurring caveat:** several entries (Littleton, Morrison, Evergreen, Golden) reference trail mileage in **Jeffco Open Space parks** near those towns rather than trails the towns themselves own or fund. This is noted in each row's description. It doesn't undercut the argument — the point is what a partnered community has *access to* — but it's exactly the kind of distinction an opposing department head will reach for, so it's better surfaced here than sprung on you in a meeting.

**Highlands Ranch is marked "No."** HRCA (Highlands Ranch Community Association) manages Backcountry Wilderness Area trails, but HRCA is a homeowners association structured as a nonprofit — not a mountain-bike trail-advocacy organization like the COMTB member groups. This distinction is called out directly in the tool's write-up.

**Source links track roughly with confidence.** When a row's confidence was raised (e.g. Parker moved from Medium to High in August 2026), it's because a primary source — usually the town's own map or page — was found and linked at the same time. If you add a source for a row, it's worth reconsidering whether the confidence badge should move too.

---

## How to update the data yourself

You don't need to touch any HTML or CSS to update a town's numbers. Open `index.html` in any text editor and search for `const DATA = [` near the top of the `<script>` block — it looks like this, one object per town:

```js
{ town:"Golden", county:"Jefferson", status:"yes", org:"COMBA", miles:48, conf:2, source:"https://www.cityofgolden.gov/community/parks_trails/index.php", note:"..." },
```

- `status` is `"yes"` or `"no"`
- `miles` is a plain number
- `conf` is `3` (High), `2` (Medium), or `1` (Low)
- `note` is the short line that appears under the town name — keep it to one or two sentences
- `source` (optional) — a URL string. If present, a small "Source ↗" link appears under the note, in both the desktop table and the mobile card view. Leave it off if you don't have a good primary source yet.
- `foothills` (optional, only meaningful on Douglas County rows) — `true` or `false`. This isn't displayed anywhere; it's used only to compute the "go it alone" thesis-strip stat, which distinguishes foothills terrain (Castle Rock, Highlands Ranch) from plains/paved-trail terrain (Parker). You only need to set this if you're adding a new Douglas County town.

**To add a new town:** copy an existing line, change every field, and add a comma. Everything else updates itself automatically — no other edits needed:
- The table, filters, sort, and mobile card view
- The **county filter chips** — these are generated from whatever counties actually appear in `DATA`, so a brand-new county gets a working filter chip with zero HTML editing
- The four **thesis-strip numbers** at the top of the page (town count, county count, partner count, and the Douglas County "go it alone" count)

**To add a new "why partner" case study** (the CAMBA / NWA Trailblazers / COMBA & Jeffco cards further down the page), search for `const CASE_STUDIES = [`, just below `DATA`. Same pattern — copy an object, change `tag`, `name`, `loc`, `stat`, `statLbl`, and `body`, add a comma. The cards render themselves; no HTML editing needed.

**To add a new color theme**, search for `const THEMES = [`. It's a two-step process now:
1. Add a new `html[data-theme="yourkey"] { ... }` block up in the `<style>` section, copying the variable list from an existing theme (sandstone, alpenglow, or meridian).
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

**Town & county primary sources (linked per-row as of August 2026):**
- Douglas County — [Castle Rock](https://www.crgov.com/1985/Open-Space-and-Trails), [Parker](https://www.parkerrec.com/301/PARKS-TRAILS), [Highlands Ranch / HRCA](https://hrcaonline.org/Recreation/Backcountry-Wilderness-Area/Trails)
- Jefferson County — [Jeffco Open Space: Deer Creek Canyon](https://www.jeffco.us/1208/Deer-Creek-Canyon-Park), [Crown Hill Park](https://www.jeffco.us/1207/Crown-Hill-Park); [Golden](https://www.cityofgolden.gov/community/parks_trails/index.php), [Lakewood / Singletracks](https://www.singletracks.com/mtb-trails/new-bike-optimized-beginner-flow-trail-opens-at-bear-creek-lake-park-near-denver-co/), [Morrison](https://www.morrisonco.us/130/Parks-Trails), [Evergreen](https://www.evergreenrecreation.com/trails), [Arvada](https://www.arvadaco.gov/508/Parks-Trails-and-Open-Space), [Conifer / CHS Today](https://chstoday.net/5669/news/new-proposed-trail-system-on-campus/)
- El Paso County — [Colorado Springs](https://coloradosprings.gov/parks-trails-open-space), [Monument](https://townofmonument.org/277/Parks-and-Open-Space-Department)
- Adams County — [Thornton](https://www.thorntonco.gov/parks-recreation/parks-planning), [Brighton](https://www.brightonco.gov/254/Parks-Recreation), [Commerce City](https://www.c3gov.com/Government/Facilities/Sand-Creek-Regional-Greenway-Commerce-City-Wetlands-Park), [Westminster](https://www.westminsterco.gov/381/Open-Space-Trails)
- Arapahoe County — [Aurora](https://www.auroragov.org/things_to_do/parks__open_space___trails), [Centennial](https://www.centennialco.gov/Government/Departments/Parks-Trails-Open-Spaces), [Englewood](https://www.englewoodco.gov/parks-recreation-library-golf/play-englewood-recreation/parks)
- Boulder County — [Boulder OSMP](https://bouldercolorado.gov/government/departments/open-space-mountain-parks)
- Clear Creek County — [Idaho Springs / Virginia Canyon Mountain Park](https://www.idahospringsco.com/home-page/page/virginia-canyon-mountain-park-vcmp)
- Gilpin County — [Black Hawk / Maryland Mountain](https://www.cityofblackhawk.org/things-do-black-hawk/page/maryland-mountain-quartz-valley-open-space-park-hiking-biking)

---

## Roadmap / ideas not yet built

- Per-capita singletrack mileage (needs population data added per town)
- 5-year trail-mileage growth rate (isolates *capacity to expand*, which is the sharper version of the Castle Rock argument)
- Grant dollars secured via nonprofit partner, where publicly documented
- Annual volunteer trail-work hours by town/org
- A "delivery model" column (in-house / contractor / nonprofit / hybrid) instead of a strict yes/no, since the strongest systems combine all three
- Since every row now carries a source link, a "last verified" date per row would be a natural next addition — it'd make the annual reverification pass much easier to track

---

## For future edits — quick orientation to the code

If you're pasting this file into a new Claude conversation to make a change, here's the shape of it: town data lives in `DATA`, the national case-study cards live in `CASE_STUDIES`, and the color themes live in `THEMES` — all three are plain arrays near the top of the `<script>` block. Everything visible on the page (the table, the filters, the county chips, the case-study cards, the theme swatches, and all four thesis-strip numbers) is generated from those three arrays at load time; none of it is hand-typed into the HTML. That means almost any data change — a new town, a new case study, a new theme, a new source link — is a one-line edit to an array, not a hunt through multiple sections of the file.

---

## Project context

Built for **Post Millennium Renaissance MTB** — [postmillenniumrenaissance.com](https://www.postmillenniumrenaissance.com) — as part of ongoing trail advocacy work in Castle Rock, Colorado. No build tooling, no dependencies, single HTML file, deploys directly to GitHub Pages.

*Last substantive data update: August 2026 (23 towns, 8 counties — added Conifer, refreshed Idaho Springs mileage, added source citations to every row). If you're reading this more than a few months later, assume at least a few mileage figures and possibly a partnership status or two have changed — reverify before citing anything in a formal setting.*
