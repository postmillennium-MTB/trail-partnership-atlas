# Colorado Trail Partnership Atlas

A single-file, no-dependency HTML tool that compares Front Range Colorado towns on whether they partner with a nonprofit trail-advocacy organization (COMBA, Medicine Wheel Trail Advocates, Boulder Mountainbike Alliance, etc.) versus building trails entirely in-house. Built as an advocacy resource for Castle Rock trail advocacy — the core argument is that partnership is the regional norm, not an ask that singles Castle Rock out.

**Live file:** `trail-partnership-atlas.html` — a single HTML file with inline CSS and JS. No build step, no npm install, no external requests except the two links in the header/footer. Drop it straight into a GitHub Pages repo.

---

## ⚠️ This data will go stale — treat it as a snapshot, not a source of truth

This is the most important thing in this README. Everything in this tool was compiled from web searches and public agency pages on **July 7, 2026**. Nearly every field in it is the kind of fact that changes:

- **Trail mileage changes constantly.** Jeffco Open Space, Colorado Springs Parks, and city departments build new trail, close trail for restoration, and reroute existing trail every season. The Golden figure (48 mi) and the Colorado Springs figure (100+ mi) are both healthy estimates, not counts — see [Data & Confidence](#data--confidence) below.
- **Partnership status can change.** A town that says "no" to a nonprofit today could sign an MOU next year — and vice versa, a partnership could lapse. This tool is exactly the kind of resource that gets stale-and-wrong quietly, which is worse than being visibly outdated.
- **Org rosters shift.** COMTB's member list, COMBA's active project list, and even the mailing addresses on Jeffco trailheads (see the Littleton/Deer Creek Canyon note in the tool) can all move.
- **New towns should get added.** This survey covers 22 municipalities across 7 counties. It is not exhaustive — it's a working sample built to make an argument, not a census.

**Recommended cadence:** re-verify the partnership-status column at least once a year, and before any formal presentation (Town Council, grant application, etc.) re-check the specific towns you're citing directly. Mileage figures are lower-priority to refresh unless you're citing an exact number out loud.

---

## What's in the tool

- **Sortable/filterable data table** — 22 towns, 7 counties, click any column header to sort, filter chips for partnership status and county, live search, and a Compact/Full detail toggle for scanning quickly on a small screen.
- **Three color themes** (Sandstone / Alpenglow / Meridian), consistent with the rest of the PMR tool suite.
- **Mobile-first table** — below 680px the table becomes stacked cards with a colored left edge (green = partner, red = no partner) instead of a horizontally-scrolling grid.
- **Write-up section** making the "why partner" case: grant eligibility, volunteer labor, trail design/sustainability, and political constituency — anchored with real numbers from COMBA, Medicine Wheel, Boulder Mountainbike Alliance, CAMBA (Wisconsin), and Northwest Arkansas/Bentonville.
- **COMTB callout** — links to the Colorado Mountain Bike Coalition and its member directory, framing local partnerships as access to a statewide network, not just a local volunteer crew.

---

## Data & Confidence

Every row carries a `conf` value (1–3) rendered as a Low/Medium/High badge:

| Confidence | Meaning |
|---|---|
| **High (3)** | Partnership status confirmed directly on the organization's own project page or a public agency record. |
| **Medium (2)** | Reasonably well-sourced but mileage is an estimate, spans multiple source disagreements, or the town/park relationship has a caveat (see below). |
| **Low (1)** | Thin sourcing — treat as a placeholder to verify, not a citable fact. |

**The recurring caveat:** several entries (Littleton, Morrison, Evergreen, and now Golden) reference trail mileage in **Jeffco Open Space parks** near those towns rather than trails the towns themselves own or fund. This is noted in each row's description. It doesn't undercut the argument — the point is what a partnered community has *access to* — but it's exactly the kind of distinction an opposing department head will reach for, so it's better surfaced here than sprung on you in a meeting.

**Highlands Ranch is marked "No."** HRCA (Highlands Ranch Community Association) manages Backcountry Wilderness Area trails, but HRCA is a homeowners association structured as a nonprofit — not a mountain-bike trail-advocacy organization like the COMTB member groups. This distinction is called out directly in the tool's write-up.

---

## How to update the data yourself

You don't need to touch any HTML or CSS to update a town's numbers. Open the file in any text editor and search for the `DATA` array near the bottom of the `<script>` block — it looks like this, one line per town:

```js
{ town:"Golden", county:"Jefferson", status:"yes", org:"COMBA", miles:48, conf:2, note:"..." },
```

- `status` is `"yes"` or `"no"`
- `miles` is a plain number
- `conf` is `3` (High), `2` (Medium), or `1` (Low)
- `note` is the short line that appears under the town name — keep it to one or two sentences

To **add a new town**, copy an existing line, change every field, and add a comma. The table, filters, sort, and mobile card view all update automatically — nothing else in the file needs to change.

If editing raw JavaScript isn't your thing, the fastest path is to paste the relevant section of this file into a Claude conversation along with whatever new information you've found (a news article, an org's project page, an updated Trailforks number) and ask for the `DATA` array to be updated. That's exactly how this file was built and revised in the first place.

---

## Sources used to build the current version

- Colorado Mountain Bike Coalition — [comtb.org](https://comtb.org) and its [member directory](https://comtb.org/colorado-trail-organizations/)
- COMBA — [comba.org](https://www.comba.org), especially the [trail systems page](https://www.comba.org/trail-systems) and project-status pages
- Medicine Wheel Trail Advocates — [medwheel.org](https://medwheel.org)
- Boulder Mountainbike Alliance — [bma-mtb.org](https://www.bma-mtb.org)
- Jefferson County Open Space — [jeffco.us](https://www.jeffco.us) park pages (Apex, North/South Table Mountain, Mt. Galbraith, Deer Creek Canyon, White Ranch, etc.)
- City of Colorado Springs Parks, Trails & Open Space — [coloradosprings.gov](https://coloradosprings.gov)
- CAMBA (Chequamegon Area Mountain Bike Association, WI) — [cambatrails.org](https://www.cambatrails.org)
- Walton Family Foundation / University of Arkansas economic impact studies on Northwest Arkansas trails
- Trailforks, COTREX, and individual city trail pages for mileage cross-checks

---

## Roadmap / ideas not yet built

- Per-capita singletrack mileage (needs population data added per town)
- 5-year trail-mileage growth rate (isolates *capacity to expand*, which is the sharper version of the Castle Rock argument)
- Grant dollars secured via nonprofit partner, where publicly documented
- Annual volunteer trail-work hours by town/org
- A "delivery model" column (in-house / contractor / nonprofit / hybrid) instead of a strict yes/no, since the strongest systems combine all three

---

## Project context

Built for **Post Millennium Renaissance MTB** — [postmillenniumrenaissance.com](https://www.postmillenniumrenaissance.com) — as part of ongoing trail advocacy work in Castle Rock, Colorado. No build tooling, no dependencies, single HTML file, deploys directly to GitHub Pages.

*Last substantive data update: July 2026. If you're reading this more than a few months later, assume at least a few mileage figures and possibly a partnership status or two have changed — reverify before citing anything in a formal setting.*
