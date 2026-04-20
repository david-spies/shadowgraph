# SHADOWGRAPH v1.4
### 6 Degrees of NASA — Geospatial Intelligence Visualization Tool

```
╔═══════════════════════════════════════════════════════════════╗
║  SHADOWGRAPH v1.4  //  6°NASA  //  OSINT CORRELATION MAP      ║
║  STATUS: UNCLASSIFIED  //  BUILD: STABLE  //  LOCAL ONLY      ║
║  36 NODES  //  78 EDGES  //  16 PATTERNS  //  2026-04-19      ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## Overview

ShadowGraph is a browser-based geospatial intelligence visualization tool for mapping spatio-temporal connections between individuals in the defense, aerospace, and national security science sectors. It implements the **6-Degrees-of-NASA** architecture — a spatial graph drill-down system that visualizes node relationships across geography, institutional affiliation, and connection type.

The tool runs entirely from a single HTML file with no backend server required. All data is embedded. An optional Node.js/Express server configuration is documented for local network deployment.

> **Current scope:** 11 core subjects (deceased or missing, 2022–2026) + 25 extended-degree nodes (institutional, oversight, and disclosure network connections). The tool does not assert confirmed connections between cases; it maps documented institutional, professional, and public-record relationships for analytical purposes.

---

## What's New in v1.4

| Version | Date | Changes |
|---|---|---|
| **v1.4** | 2026-04-19 | Amy Eskridge (Case 11) full integration. Added Richard Eskridge (1°), Franc Milburn (2°), Michael Shellenberger (3°). New ANTIGRAVITY_UAP pattern. 10 new edges. Header corrected to 36 nodes / 78 edges / 6 deceased / 3 missing. |
| v1.3 | 2026-04-17 | Steven Garcia (Case 10) added as core node. Karoline Leavitt (4°) added. NUCLEAR_WEAPONS_COMPLEX pattern. 8 new edges. |
| v1.2 | 2026-04-08 | 4°–6° degree nodes added: Leshin, Johnson, Burchett, Burlison, Swecker, DeLonge, Elizondo, Gallagher, Chesley, Chabot. Degree filter buttons extended to 6°. 33 edges added. |
| v1.1 | 2026-04-08 | Syntax fix (premature `];` in NODES_EXT). Degree filter buttons corrected. All degree nodes rendering properly. |
| v1.0 | 2026-04-05 | Initial release — 7 core nodes, 8 edges, map + graph modes. |

---

## Features

| Feature | Description |
|---|---|
| **Geospatial Map** | Leaflet.js dark tile map with custom status-coded and degree-coded markers |
| **Force-Directed Graph** | D3.js network graph with draggable nodes, physics simulation, and degree legend |
| **6-Degree Node System** | CORE (incident subjects) through 6° extended connections, all visually distinct |
| **Drill-Down Intel Panel** | Click any node for full intelligence brief, sourced timeline, and OSINT links |
| **Edge Filtering** | Toggle WORK, ACQUAINTANCE, and INSTITUTIONAL connection types independently |
| **Status Filtering** | Filter by ALL / DECEASED / MISSING |
| **Degree Filtering** | Filter by ALL DEG / CORE / 1° / 2° / 3° / 4° / 5° / 6° |
| **Pattern Clusters** | 16 named pattern clusters, each highlighting a subnetwork of related nodes |
| **Live HUD** | Real-time UTC clock, zoom level, visible node count |
| **OSINT Source Links** | Per-node links to verified news articles and primary sources |
| **RESET Button** | Clears all filters and restores full view |
| **Tech-Noir UI** | Solarized-green / slate-blue / black aesthetic with scan-line overlay |

---

## Subjects Indexed (v1.4)

### Core Subjects — Degree 0 (Incident Subjects)

| ID | Name | Organization | Status |
|---|---|---|---|
| `ESKRIDGE` | Amy Eskridge | Institute for Exotic Science / HoloChron Engineering | DECEASED — Jun 11, 2022 |
| `HICKS` | Michael David Hicks | NASA JPL — Research Scientist | DECEASED — Jul 30, 2023 |
| `MAIWALD` | Frank Maiwald | NASA JPL — Technical Group Supervisor | DECEASED — Jul 4, 2024 |
| `CHAVEZ` | Anthony Chavez | Los Alamos National Laboratory (Ret.) | ACTIVE — Missing May 8, 2025 |
| `REZA` | Monica Reza | NASA JPL — Director, Materials Processing | MISSING — Jun 22, 2025 |
| `CASIAS` | Melissa Casias | Los Alamos National Laboratory | ACTIVE — Missing Jun 26, 2025 |
| `GARCIA` | Steven Garcia | Kansas City National Security Campus (KCNSC) | MISSING — Aug 28, 2025 |
| `THOMAS` | Jason Thomas | Novartis — Asst. Director, Chemical Biology | DECEASED — Dec 12, 2025 |
| `LOUREIRO` | Nuno Loureiro | MIT — Plasma Science & Fusion Center | DECEASED — Dec 16, 2025 |
| `GRILLMAIR` | Carl Grillmair | Caltech / IPAC | DECEASED — Feb 16, 2026 |
| `MCCASLAND` | William McCasland | USAF (Ret.) / AFRL — Former Commander | MISSING — Feb 27, 2026 |

**Deceased: 6 &nbsp;|&nbsp; Missing: 3 &nbsp;|&nbsp; Active (status unconfirmed): 2**

> CASIAS and CHAVEZ are listed ACTIVE in the system as no confirmed death has been established, but both remain unaccounted for. GARCIA is formally listed MISSING by Albuquerque police.

---

### 1st Degree — Direct Institutional / Family Links

| ID | Name | Organization | Connection Basis |
|---|---|---|---|
| `ELACHI` | Dr. Charles Elachi | NASA JPL (Director 2001–2016) / Caltech | Directed JPL during tenures of HICKS, MAIWALD, REZA |
| `HARRISON` | Dr. Fiona A. Harrison | Caltech — PMA Division Chair (2015–2025) | Chaired Caltech division housing GRILLMAIR's IPAC |
| `RAYMOND` | Gen. John W. Raymond | US Space Force — 1st Chief of Space Operations | Successive USAF command chain with MCCASLAND |
| `RICHARD_ESKRIDGE` | Richard Eskridge | NASA MSFC (Ret.) / HoloChron Engineering | Father and co-founder of Institute for Exotic Science; CTO |
| `ZUBER` | Dr. Maria Zuber | MIT — Former VP for Research (2013–2024) | Directly oversaw MIT PSFC (LOUREIRO's center) |

---

### 2nd Degree — Extended Institutional Network

| ID | Name | Organization | Connection Basis |
|---|---|---|---|
| `BHATTACHARJEE` | Dr. Amitava Bhattacharjee | Princeton / PPPL | Shared plasma physics domain with LOUREIRO |
| `HELMS` | Lt. Gen. Susan Helms | USAF (Ret.) — 14th Air Force Commander | Predecessor command to RAYMOND; overlaps MCCASLAND chain |
| `MASON` | Thomas Mason | LANL (Former Director, 2006–2018) | Built the institutional structure CASIAS and CHAVEZ worked within |
| `MILBURN` | Franc Milburn | Retired British Intelligence | Investigated ESKRIDGE; conclusions submitted to Congress 2023 |
| `WATKINS` | Dr. Michael Watkins | NASA JPL (Director 2016–2021) | Succeeded ELACHI; established JPL structure REZA joined |

---

### 3rd Degree — Policy, Science & Oversight Chain

| ID | Name | Organization | Connection Basis |
|---|---|---|---|
| `GRUNSFELD` | Dr. John Grunsfeld | NASA — Science Mission Directorate | Oversaw JPL science missions; concurrent leadership with ELACHI |
| `LANDER` | Dr. Eric Lander | Broad Institute / MIT | Federal science policy; MIT institutional network with LOUREIRO |
| `PRABHAKAR` | Dr. Arati Prabhakar | OSTP / Former DARPA Director | DARPA–LANL–MIT funding chains; OSTP federal coordination |
| `SHELLENBERGER` | Michael Shellenberger | Journalist / Congressional Witness | Testified at UAP hearing; formally entered MILBURN/ESKRIDGE findings into congressional record |

---

### 4th Degree — Government Response & Oversight Layer

| ID | Name | Organization | Connection Basis |
|---|---|---|---|
| `BURCHETT` | Rep. Tim Burchett | U.S. House — TN 2nd District | House UAP Subcommittee; primary congressional voice on the pattern |
| `BURLISON` | Rep. Eric Burlison | U.S. House — MO 7th District | Formally requested FBI investigation; House Oversight Committee |
| `JOHNSON_L` | Lindley Johnson | NASA HQ — Planetary Defense Officer (Emeritus) | Led PDCO; oversaw DART/NEO programs HICKS and GRILLMAIR served on |
| `LEAVITT` | Karoline Leavitt | White House Press Secretary (2025–present) | First WH official to formally acknowledge pattern on record (Apr 16, 2026) |
| `LESHIN` | Dr. Laurie Leshin | NASA JPL (Director 2022–2025) / Caltech | Directed JPL during MAIWALD's death (Jul 2024) and REZA's disappearance (Jun 2025) |
| `SWECKER` | Chris Swecker | FBI (Ret.) — Asst. Director, Criminal Investigative Division | Named foreign intelligence targeting; primary law enforcement commentator |

---

### 5th Degree — UAP Disclosure Network

| ID | Name | Organization | Connection Basis |
|---|---|---|---|
| `DELONGE` | Tom DeLonge | To The Stars Inc. — Founder & CEO | Documented 2016 meeting with MCCASLAND (Podesta emails); TTSA UAP platform |
| `ELIZONDO` | Luis Elizondo | Pentagon AATIP (Former) / Independent | Senior AATIP figure; connected to TTSA / DELONGE / MCCASLAND |
| `GALLAGHER` | Dave Gallagher | NASA JPL — 11th Director (Jun 2025–present) | Became JPL Director Jun 2, 2025 — 20 days before REZA vanished |

---

### 6th Degree — Mission Science Chain

| ID | Name | Organization | Connection Basis |
|---|---|---|---|
| `CHABOT` | Dr. Nancy Chabot | Johns Hopkins APL — DART Coordination Lead | DART mission lead; APL institutional counterpart to HICKS's JPL science team |
| `CHESLEY` | Dr. Steve Chesley | NASA JPL — CNEOS Senior Scientist | Led JPL DART science investigation; direct science chain to HICKS |

---

## Pattern Clusters (v1.4)

16 named pattern clusters selectable from the Pattern Clusters panel.

| Pattern ID | Label | Key Nodes | Color |
|---|---|---|---|
| `PASADENA_TRIANGLE` | Pasadena Triangle | GRILLMAIR, MAIWALD, REZA, HICKS, ELACHI, HARRISON, WATKINS | Teal |
| `JPL_LEADERSHIP` | JPL Leadership Chain | ELACHI, WATKINS, GRUNSFELD, REZA, GRILLMAIR, MAIWALD, HICKS | Blue |
| `POWER_AXIS` | Power Axis (Military–NASA) | MCCASLAND, REZA, RAYMOND, HELMS | Red |
| `SPACE_COMMAND_CHAIN` | Space Command Chain | MCCASLAND, RAYMOND, HELMS | Amber |
| `PLASMA_NETWORK` | Plasma Physics Network | LOUREIRO, BHATTACHARJEE, ZUBER, RICHARD_ESKRIDGE | Violet |
| `MIT_CORE` | MIT Institutional Core | LOUREIRO, ZUBER, LANDER, THOMAS | Orange |
| `NM_CORRIDOR` | New Mexico Corridor | MCCASLAND, CASIAS, CHAVEZ, GARCIA, MASON | Solarized-green |
| `DOE_FUSION_CHAIN` | DOE Fusion Chain | LOUREIRO, BHATTACHARJEE, PRABHAKAR, CHAVEZ | Pink |
| `FEDERAL_SCIENCE_POLICY` | Federal Science Policy | PRABHAKAR, LANDER, GRUNSFELD, THOMAS | Grey |
| `INCIDENT_TIMELINE` | Incident Timeline 2022–2026 | All 11 core subjects | Red |
| `PLANETARY_DEFENSE` | Planetary Defense Network | HICKS, GRILLMAIR, JOHNSON_L, LESHIN, CHESLEY, CHABOT, ELACHI, WATKINS | Blue |
| `CONGRESSIONAL_OVERSIGHT` | Congressional Oversight | BURCHETT, BURLISON, SWECKER, SHELLENBERGER, MCCASLAND, REZA, GRILLMAIR, LOUREIRO | Amber |
| `UAP_NETWORK` | UAP Research Network | ESKRIDGE, MCCASLAND, DELONGE, ELIZONDO, RAYMOND, BURCHETT, BURLISON | Violet |
| `INTEL_OVERSIGHT` | Intel & Law Enforcement | SWECKER, ELIZONDO, MILBURN, BURCHETT, BURLISON, MCCASLAND | Red |
| `NUCLEAR_WEAPONS_COMPLEX` | Nuclear Weapons Complex | GARCIA, CASIAS, CHAVEZ, MCCASLAND, MASON | Red |
| `ANTIGRAVITY_UAP` | Anti-Gravity / UAP Disclosure | ESKRIDGE, RICHARD_ESKRIDGE, MILBURN, SHELLENBERGER, DELONGE, MCCASLAND, ELIZONDO | Pink |

---

## Connection Graph (v1.4)

### Core Edges — Degree 0 Direct Connections

```
MCCASLAND      ──[WORK]──────────────────── REZA
CASIAS         ──[WORK]──────────────────── CHAVEZ
MAIWALD        ──[ACQUAINTANCE]──────────── GRILLMAIR
LOUREIRO       ──[ACQUAINTANCE]──────────── CHAVEZ
GRILLMAIR      ──[ACQUAINTANCE]──────────── LOUREIRO
REZA           ──[INSTITUTIONAL]──────────── MAIWALD
MCCASLAND      ──[INSTITUTIONAL]──────────── GRILLMAIR
CASIAS         ──[INSTITUTIONAL]──────────── LOUREIRO
HICKS          ──[WORK]──────────────────── MAIWALD
HICKS          ──[WORK]──────────────────── GRILLMAIR
HICKS          ──[INSTITUTIONAL]──────────── REZA
THOMAS         ──[ACQUAINTANCE]──────────── LOUREIRO
```

### 1st Degree Edges

```
ELACHI         ──[INSTITUTIONAL]──────────── REZA
ELACHI         ──[INSTITUTIONAL]──────────── GRILLMAIR
HICKS          ──[INSTITUTIONAL]──────────── ELACHI
RAYMOND        ──[WORK]──────────────────── MCCASLAND
ZUBER          ──[INSTITUTIONAL]──────────── LOUREIRO
HARRISON       ──[INSTITUTIONAL]──────────── GRILLMAIR
RICHARD_ESKRIDGE ──[ACQUAINTANCE]────────── LOUREIRO
ESKRIDGE       ──[WORK]──────────────────── RICHARD_ESKRIDGE
```

### 2nd Degree Edges

```
BHATTACHARJEE  ──[ACQUAINTANCE]──────────── LOUREIRO
HELMS          ──[WORK]──────────────────── MCCASLAND
HELMS          ──[WORK]──────────────────── RAYMOND
WATKINS        ──[INSTITUTIONAL]──────────── REZA
WATKINS        ──[INSTITUTIONAL]──────────── ELACHI
MASON          ──[WORK]──────────────────── CHAVEZ
MASON          ──[WORK]──────────────────── CASIAS
MILBURN        ──[WORK]──────────────────── SHELLENBERGER
MILBURN        ──[INSTITUTIONAL]──────────── BURCHETT
MILBURN        ──[INSTITUTIONAL]──────────── BURLISON
ESKRIDGE       ──[WORK]──────────────────── MILBURN
GARCIA         ──[INSTITUTIONAL]──────────── MASON
```

### 3rd Degree Edges

```
GRUNSFELD      ──[INSTITUTIONAL]──────────── REZA
GRUNSFELD      ──[INSTITUTIONAL]──────────── ELACHI
LANDER         ──[INSTITUTIONAL]──────────── LOUREIRO
THOMAS         ──[INSTITUTIONAL]──────────── LANDER
PRABHAKAR      ──[INSTITUTIONAL]──────────── CHAVEZ
PRABHAKAR      ──[INSTITUTIONAL]──────────── LOUREIRO
SHELLENBERGER  ──[INSTITUTIONAL]──────────── BURCHETT
SHELLENBERGER  ──[ACQUAINTANCE]──────────── ELIZONDO
```

### 4th Degree Edges

```
LESHIN         ──[INSTITUTIONAL]──────────── REZA
LESHIN         ──[INSTITUTIONAL]──────────── MAIWALD
LESHIN         ──[INSTITUTIONAL]──────────── GRILLMAIR
LESHIN         ──[INSTITUTIONAL]──────────── WATKINS
JOHNSON_L      ──[WORK]──────────────────── HICKS
JOHNSON_L      ──[WORK]──────────────────── GRILLMAIR
JOHNSON_L      ──[INSTITUTIONAL]──────────── LESHIN
BURCHETT       ──[ACQUAINTANCE]──────────── MCCASLAND
BURCHETT       ──[ACQUAINTANCE]──────────── GRILLMAIR
BURCHETT       ──[ACQUAINTANCE]──────────── LOUREIRO
BURLISON       ──[ACQUAINTANCE]──────────── MCCASLAND
BURLISON       ──[ACQUAINTANCE]──────────── REZA
BURLISON       ──[WORK]──────────────────── BURCHETT
SWECKER        ──[ACQUAINTANCE]──────────── GRILLMAIR
SWECKER        ──[ACQUAINTANCE]──────────── MCCASLAND
SWECKER        ──[ACQUAINTANCE]──────────── BURCHETT
LEAVITT        ──[ACQUAINTANCE]──────────── GARCIA
LEAVITT        ──[INSTITUTIONAL]──────────── BURCHETT
LEAVITT        ──[INSTITUTIONAL]──────────── BURLISON
LEAVITT        ──[ACQUAINTANCE]──────────── SWECKER
```

### 5th Degree Edges

```
DELONGE        ──[WORK]──────────────────── MCCASLAND
DELONGE        ──[ACQUAINTANCE]──────────── RAYMOND
ELIZONDO       ──[ACQUAINTANCE]──────────── MCCASLAND
ELIZONDO       ──[WORK]──────────────────── DELONGE
ELIZONDO       ──[ACQUAINTANCE]──────────── BURCHETT
GALLAGHER      ──[INSTITUTIONAL]──────────── REZA
GALLAGHER      ──[INSTITUTIONAL]──────────── LESHIN
GALLAGHER      ──[INSTITUTIONAL]──────────── GRILLMAIR
ESKRIDGE       ──[ACQUAINTANCE]──────────── MCCASLAND
ESKRIDGE       ──[ACQUAINTANCE]──────────── DELONGE
```

### 6th Degree Edges

```
CHESLEY        ──[WORK]──────────────────── HICKS
CHESLEY        ──[INSTITUTIONAL]──────────── JOHNSON_L
CHESLEY        ──[INSTITUTIONAL]──────────── GRILLMAIR
CHABOT         ──[WORK]──────────────────── HICKS
CHABOT         ──[WORK]──────────────────── CHESLEY
```

### Additional Cross-Cluster Edges

```
GARCIA         ──[ACQUAINTANCE]──────────── MCCASLAND
GARCIA         ──[ACQUAINTANCE]──────────── CASIAS
GARCIA         ──[ACQUAINTANCE]──────────── CHAVEZ
```

**Edge color coding:**
- `#268bd2` Blue — WORK (direct professional collaboration or command oversight)
- `#6c71c4` Violet dashed — ACQUAINTANCE (documented peer-level or community link)
- `#2aa198` Teal dotted — INSTITUTIONAL (shared org, program, or academic pipeline)

---

## Incident Timeline

| Date | ID | Subject | Institution | Status |
|---|---|---|---|---|
| Jun 11, 2022 | `ESKRIDGE` | Amy Eskridge | Institute for Exotic Science | DECEASED (official: suicide; contested by Milburn findings submitted to Congress) |
| Jul 30, 2023 | `HICKS` | Michael David Hicks | NASA JPL | DECEASED (cause undisclosed) |
| Jul 4, 2024 | `MAIWALD` | Frank Maiwald | NASA JPL | DECEASED (cause undisclosed; no autopsy performed) |
| May 8, 2025 | `CHAVEZ` | Anthony Chavez | Los Alamos National Laboratory | MISSING |
| Jun 22, 2025 | `REZA` | Monica Reza | NASA JPL | MISSING (Angeles National Forest) |
| Jun 26, 2025 | `CASIAS` | Melissa Casias | Los Alamos National Laboratory | MISSING (devices factory-reset) |
| Aug 28, 2025 | `GARCIA` | Steven Garcia | KCNSC Albuquerque | MISSING (left home on foot carrying handgun) |
| Dec 12, 2025 | `THOMAS` | Jason Thomas | Novartis | DECEASED (body found Mar 17, 2026; no foul play suspected) |
| Dec 16, 2025 | `LOUREIRO` | Nuno Loureiro | MIT PSFC | DECEASED (shot at home; assailant identified, died of suicide) |
| Feb 16, 2026 | `GRILLMAIR` | Carl Grillmair | Caltech / IPAC | DECEASED (shot at home; suspect arrested on murder charge) |
| Feb 27, 2026 | `MCCASLAND` | William McCasland | USAF (Ret.) / AFRL | MISSING (left Albuquerque on foot; left phone/glasses; had .38 revolver) |

> **IMPORTANT:** No official investigation has confirmed any connection between these cases. The White House acknowledged the pattern on April 16, 2026. President Trump stated "pretty serious stuff" and confirmed a meeting on the subject on April 17, 2026. The FBI, NNSA, and multiple congressional offices are conducting independent reviews as of April 19, 2026.

---

## Tech Stack

```
Frontend
├── HTML5 / CSS3 / Vanilla JS       — Single-file architecture, no build step
├── Leaflet.js 1.9.4                — Geospatial map engine
│   └── CDN: cdnjs.cloudflare.com
├── D3.js 7.8.5                     — Force-directed graph engine
│   └── CDN: cdnjs.cloudflare.com
├── CartoDB Dark Matter tiles       — Map tile layer (requires internet)
└── Google Fonts (optional)         — Share Tech Mono, Rajdhani, Orbitron
    └── Fallback: Courier New, Trebuchet MS

Optional Backend (Node.js)
├── Node.js >= 18.x
├── Express 4.x                     — Static file server
└── (Future) better-sqlite3         — Local encrypted data store
```

---

## Project File Structure

```
shadowgraph/
│
├── shadowgraph.html          ← PRIMARY APPLICATION FILE (open this)
│
├── README.md                 ← This file (v1.4)
├── QUICKSTART.md             ← Step-by-step setup guide
│
├── server/                   ← Optional Node.js backend
│   ├── server.js             ← Express static server
│   ├── package.json          ← Node dependencies
│   └── package-lock.json     ← Lockfile (auto-generated)
│
├── data/                     ← Future: external data files
│   ├── nodes.json            ← Node dataset (exportable from HTML)
│   └── edges.json            ← Edge dataset (exportable from HTML)
│
└── docs/                     ← Documentation
    ├── ARCHITECTURE.md       ← System design notes
    └── DATA_SCHEMA.md        ← Node/edge schema reference
```

---

## Data Schema

### Node Object (v1.4)

```javascript
{
  id:       'ESKRIDGE',                         // Unique uppercase string key
  name:     'Amy Eskridge',                     // Full display name
  lat:      34.730,                             // Latitude (decimal degrees)
  lng:      -86.586,                            // Longitude (decimal degrees)
  status:   'DECEASED',                         // 'DECEASED' | 'MISSING' | 'ACTIVE'
  degree:   0,                                  // 0=core, 1–6=extended (omit for core)
  cluster:  'AEROSPACE',                        // Pattern cluster label
  field:    'Aerospace / Anti-Gravity / UAP',   // Research or professional domain
  org:      'Institute for Exotic Science',     // Organization
  location: 'Huntsville, AL',                  // Human-readable location
  date:     'Jun 11, 2022',                    // Incident date or 'N/A'
  patterns: ['INCIDENT_TIMELINE','UAP_NETWORK','ANTIGRAVITY_UAP'],
  summary:  '...',                              // Professional biography (OSINT-sourced)
  cause:    '...',                              // Incident description
  links: [
    { label: 'Display Name', url: 'https://...' }
  ],
  timeline: [
    { date: 'YYYY', event: 'Description' }
  ]
}
```

### Edge Object

```javascript
{
  source: 'ESKRIDGE',          // Source node ID
  target: 'MILBURN',           // Target node ID
  type:   'WORK',              // 'WORK' | 'ACQUAINTANCE' | 'INSTITUTIONAL'
  label:  'Description'        // Tooltip and intel panel text
}
```

### Pattern Object

```javascript
ANTIGRAVITY_UAP: {
  id:    'ANTIGRAVITY_UAP',
  label: 'Anti-Gravity / UAP Disclosure Network',
  color: '#d33682',
  desc:  'The Eskridge-centered anti-gravity and UAP disclosure cluster...',
  nodes: ['ESKRIDGE','RICHARD_ESKRIDGE','MILBURN','SHELLENBERGER',
          'DELONGE','MCCASLAND','ELIZONDO']
}
```

---

## Adding New Nodes

Open `shadowgraph.html` in a text editor. Locate `const NODES = [` for core subjects (degree 0) or `const NODES_EXT = [` for extended nodes (degree 1–6). Follow the schema exactly. Use single-quoted JS strings; escape all apostrophes within field values as `\'`.

## Adding New Edges

Locate `const EDGES = [`. Add an entry with valid `source` and `target` IDs and `type` of `WORK`, `ACQUAINTANCE`, or `INSTITUTIONAL`.

## Adding New Patterns

Locate `const PATTERNS = {`. Add a key following the pattern object schema. Add the pattern ID string to the `patterns:` array of each member node.

---

## Browser Compatibility

| Browser | Version | Status |
|---|---|---|
| Chrome / Chromium | 90+ | ✓ Fully supported |
| Firefox | 88+ | ✓ Fully supported |
| Safari | 14+ | ✓ Supported |
| Edge (Chromium) | 90+ | ✓ Fully supported |
| Internet Explorer | Any | ✗ Not supported |

---

## Network Requirements

| Resource | Domain | Required | Notes |
|---|---|---|---|
| Leaflet JS/CSS | cdnjs.cloudflare.com | **Yes** | Core map library |
| D3.js | cdnjs.cloudflare.com | **Yes** | Core graph library |
| Map Tiles | basemaps.cartocdn.com | **Yes** | Visible map imagery |
| Fonts | fonts.googleapis.com | No | Falls back to system fonts |

For **fully offline operation**, see `QUICKSTART.md` → Section 4: Offline Mode.

---

## Security Notes

- All data is stored client-side within the HTML file. No data is transmitted to any server.
- The tool does not set cookies, use localStorage, or make API calls beyond CDN asset loading and tile fetching.
- For sensitive operational use, serve via the local Node.js server on `localhost` only.
- All subject data is sourced exclusively from publicly available news reporting, obituaries, congressional records, and official statements. No classified information is contained herein.

---

## Dependencies

### Runtime (CDN — requires internet)

| Library | Version | Source | Purpose |
|---|---|---|---|
| Leaflet.js | 1.9.4 | cdnjs.cloudflare.com | Geospatial map rendering |
| Leaflet CSS | 1.9.4 | cdnjs.cloudflare.com | Map UI styling |
| D3.js | 7.8.5 | cdnjs.cloudflare.com | Force graph simulation |
| CartoDB Tiles | — | basemaps.cartocdn.com | Dark map tiles |
| Google Fonts | — | fonts.googleapis.com | Typography (optional) |

### Optional Backend (npm)

| Package | Version | Purpose |
|---|---|---|
| express | ^4.18.0 | Local HTTP server |
| better-sqlite3 | ^9.0.0 | Local database (future) |
| nodemon | ^3.0.0 | Dev auto-reload (devDependency) |

---

## Version History

| Version | Date | Nodes | Edges | Patterns | Notes |
|---|---|---|---|---|---|
| **v1.4** | **2026-04-19** | **36** | **78** | **16** | **Eskridge (Case 11) + Richard Eskridge (1°) + Milburn (2°) + Shellenberger (3°). ANTIGRAVITY_UAP pattern. Header corrected.** |
| v1.3 | 2026-04-17 | 32 | 68 | 15 | Garcia (Case 10) + Leavitt (4°). NUCLEAR_WEAPONS_COMPLEX pattern. |
| v1.2 | 2026-04-08 | 29 | 60 | 14 | 4°–6° degree nodes. Degree filter buttons extended to 6°. |
| v1.1 | 2026-04-08 | 29 | 60 | 14 | Syntax fix. Degree filters corrected. |
| v1.0 | 2026-04-05 |  7 |  8 |  0 | Initial release. |

---

*SHADOWGRAPH // 6°NASA // v1.4 // BUILD STABLE // OSINT ONLY // 2026-04-19*
