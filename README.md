<img width="1136" height="640" alt="ShadowGraph_v3" src="https://github.com/user-attachments/assets/a2b45dbe-190f-4c3c-b8e7-7813f83a3d4f" />

# SHADOWGRAPH v1.3
### 6 Degrees of NASA — Geospatial Intelligence Visualization Tool

```
╔═══════════════════════════════════════════════════════════╗
║  SHADOWGRAPH v1.3  //  6°NASA  //  OSINT CORRELATION MAP  ║
║  STATUS: UNCLASSIFIED  //  BUILD: STABLE  //  LOCAL ONLY  ║
╚═══════════════════════════════════════════════════════════╝
```

---

## Overview

ShadowGraph is a lightweight, browser-based geospatial intelligence visualization tool for mapping spatio-temporal connections between individuals in the defense, aerospace, and national security science sectors. It implements the **6-Degrees-of-NASA** architecture — a spatial graph drill-down system that visualizes node relationships across geography, institutional affiliation, and connection type.

The tool runs entirely from a single HTML file with no backend server required. All data is embedded. An optional Node.js/Express server configuration is documented for local network deployment or future SQLite integration.

---

## Features

| Feature | Description |
|---|---|
| **Geospatial Map** | Leaflet.js dark tile map with custom status-coded markers |
| **Force-Directed Graph** | D3.js network graph with draggable nodes and physics simulation |
| **Drill-Down Intel Panel** | Click any node to expand full intelligence brief, timeline, and source links |
| **Edge Filtering** | Toggle Work, Acquaintance, and Institutional connection types independently |
| **Node Filtering** | Filter subjects by status: All / Deceased / Missing |
| **Live HUD** | Real-time UTC clock, zoom level, visible node count |
| **OSINT Links** | Direct links to verified news articles and primary sources per subject |
| **Tech-Noir UI** | Solarized-green / slate-blue / black aesthetic with scan-line overlay |
| **Font Fallbacks** | Degrades gracefully to system monospace fonts if Google Fonts is unavailable |

---

## Subjects Indexed (v1.0)

| ID | Name | Organization | Status |
|---|---|---|---|
| `GRILLMAIR` | Carl Grillmair | Caltech / IPAC | DECEASED — Feb 16, 2026 |
| `LOUREIRO` | Nuno Loureiro | MIT — Plasma Science & Fusion Center | DECEASED — Dec 16, 2025 |
| `REZA` | Monica Reza | NASA JPL / Aerojet Rocketdyne | MISSING — Jun 22, 2025 |
| `MCCASLAND` | William McCasland | USAF (Ret.) / AFRL | MISSING — Feb 27, 2026 |
| `CASIAS` | Melissa Casias | Los Alamos National Laboratory | ACTIVE |
| `CHAVEZ` | Anthony Chavez | Los Alamos National Laboratory | ACTIVE |
| `MAIWALD` | Frank Maiwald | NASA JPL | ACTIVE |

---

## Connection Graph (v1.0)

```
MCCASLAND ──[WORK]────────────── REZA
CASIAS    ──[WORK]────────────── CHAVEZ
MAIWALD   ──[ACQUAINTANCE]────── GRILLMAIR
LOUREIRO  ──[ACQUAINTANCE]────── CHAVEZ
GRILLMAIR ──[ACQUAINTANCE]────── LOUREIRO
REZA      ──[INSTITUTIONAL]───── MAIWALD
MCCASLAND ──[INSTITUTIONAL]───── GRILLMAIR
CASIAS    ──[INSTITUTIONAL]───── LOUREIRO
```

**Edge color coding:**
- `#268bd2` Blue — Work (direct professional collaboration or oversight)
- `#6c71c4` Violet dashed — Acquaintance (known peer-level or community link)
- `#2aa198` Teal dotted — Institutional (shared org, program, or academic pipeline)

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
├── README.md                 ← This file
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
├── assets/                   ← Future: local static assets
│   ├── fonts/                ← Local font files (offline fallback)
│   └── tiles/                ← Future: offline map tile cache
│
└── docs/                     ← Documentation
    ├── ARCHITECTURE.md       ← System design notes
    └── DATA_SCHEMA.md        ← Node/edge schema reference
```

> **Minimum deployment:** Only `shadowgraph.html` is required to run the tool. All other directories support future expansion.

---

## Dependencies

### Runtime (CDN — requires internet on first load)

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

## Data Schema

### Node Object
```javascript
{
  id:       'GRILLMAIR',                    // Unique uppercase string key
  name:     'Carl Grillmair',               // Full display name
  lat:      34.475,                         // Latitude (decimal degrees)
  lng:      -117.828,                       // Longitude (decimal degrees)
  status:   'DECEASED',                     // 'DECEASED' | 'MISSING' | 'ACTIVE'
  field:    'Astrophysics / Galactic Astronomy',
  org:      'Caltech / IPAC',
  location: 'Llano, CA (Antelope Valley)',  // Human-readable location
  date:     'Feb 16, 2026',                 // Incident date or 'N/A'
  summary:  '...',                          // Professional biography
  cause:    '...',                          // Incident description
  links: [                                  // Array of OSINT source links
    { label: 'Display Name', url: 'https://...' }
  ],
  timeline: [                               // Chronological event log
    { date: 'YYYY', event: 'Description' }
  ]
}
```

### Edge Object
```javascript
{
  source: 'MCCASLAND',           // Source node ID
  target: 'REZA',                // Target node ID
  type:   'WORK',                // 'WORK' | 'ACQUAINTANCE' | 'INSTITUTIONAL'
  label:  'Description of link'  // Displayed in tooltip and detail panel
}
```

---

## Browser Compatibility

| Browser | Version | Status |
|---|---|---|
| Chrome / Chromium | 90+ | ✓ Fully supported |
| Firefox | 88+ | ✓ Fully supported |
| Safari | 14+ | ✓ Supported |
| Edge (Chromium) | 90+ | ✓ Fully supported |
| Internet Explorer | Any | ✗ Not supported |

> **Note:** The tool requires JavaScript enabled. It does not function in environments with strict Content Security Policies that block `cdnjs.cloudflare.com` or `basemaps.cartocdn.com`.

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

## Adding New Nodes

Open `shadowgraph.html` in a text editor. Locate the `NODES` array (search for `const NODES = [`). Add a new entry following the schema above. Latitude/longitude coordinates can be obtained from [Google Maps](https://maps.google.com) by right-clicking any location.

## Adding New Edges

Locate the `EDGES` array (search for `const EDGES = [`). Add a new entry using the `source` and `target` IDs from existing nodes. Valid `type` values are `WORK`, `ACQUAINTANCE`, or `INSTITUTIONAL`.

---

## Security Notes

- All data is stored client-side within the HTML file. No data is transmitted to any server.
- The tool does not set cookies, use localStorage, or make API calls beyond CDN asset loading and tile fetching.
- For sensitive operational use, serve via the local Node.js server on `localhost` only (do not expose to external networks).
- The optional SQLite backend, if implemented, should use an encrypted extension (e.g., `sqlcipher`) for data at rest.

---

## License

This tool was developed for open-source intelligence research and educational visualization purposes. All subject data is sourced from publicly available news reporting and official statements. No classified information is contained herein.

---

## Version History

| Version | Date | Notes |
|---|---|---|
| v1.0 | 2026-04-05 | Initial release ————— 7 nodes,  8 connections, 8 edges, map + graph modes |
| v1.1 | 2026-04-06 | subsequent release — 18 nodes, 26 connections, 8 edges, map + graph modes |
| v1.2 | 2026-04-07 | subsequent release — 20 nodes, 32 connections, 8 edges, map + graph modes |
| v1.3 | 2026-04-08 | subsequent release — 29 nodes, 65 connections, 8 edges, map + graph modes |
---

*SHADOWGRAPH // 6°NASA // BUILD STABLE // OSINT ONLY*
