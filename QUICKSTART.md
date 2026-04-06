# QUICKSTART — SHADOWGRAPH v1.0

```
╔══════════════════════════════════════════╗
║  SHADOWGRAPH // QUICKSTART GUIDE         ║
║  EST. SETUP TIME: 2–10 MIN               ║
║  SKILL LEVEL: BEGINNER → INTERMEDIATE    ║
╚══════════════════════════════════════════╝
```

---

## Choose Your Setup Path

| Path | Time | Requires | Best For |
|---|---|---|---|
| **[Option A]** Double-click (browser) | 2 min | Nothing | Quick local use |
| **[Option B]** Python server | 3 min | Python 3 | Reliable local serving |
| **[Option C]** Node.js server | 10 min | Node.js 18+ | Dev mode + future backend |
| **[Option D]** Offline mode | 15 min | Node.js + npm | Air-gapped / no internet |

---

## Prerequisites — What You Need

Before starting, confirm you have the following files from the ShadowGraph release:

```
shadowgraph.html      ← Required for all options
README.md             ← Reference documentation
QUICKSTART.md         ← This file
```

---

## Option A — Double-Click (Simplest)

This works for immediate local use. No installation required.

**Step 1.** Place `shadowgraph.html` anywhere on your machine. A dedicated folder is recommended:

```
# Recommended directory structure
~/shadowgraph/
└── shadowgraph.html
```

**Step 2.** Double-click `shadowgraph.html`. It will open in your default browser.

**Step 3.** If the map does not load:
- Confirm you have an active internet connection (required for map tiles and library CDNs)
- If Chrome shows a blank map, right-click the page → Inspect → Console tab — look for errors
- Try opening in Firefox if Chrome blocks local file scripts

> **Limitation:** Some browsers (especially Chrome) restrict certain JavaScript APIs when opening files directly via `file://`. If you see CSP errors or a broken layout, use Option B or C instead.

---

## Option B — Python Local Server (Recommended for Most Users)

Python's built-in HTTP server eliminates all `file://` protocol restrictions in one command.

**Requirements:** Python 3.6 or later. Verify with:
```bash
python3 --version
# Expected output: Python 3.x.x
```

**Step 1.** Create your project folder and place the file:

```bash
mkdir -p ~/shadowgraph
cp shadowgraph.html ~/shadowgraph/
cd ~/shadowgraph
```

**Step 2.** Start the server:

```bash
python3 -m http.server 8080
```

You should see:
```
Serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8080/) ...
```

**Step 3.** Open your browser and navigate to:

```
http://localhost:8080/shadowgraph.html
```

**Step 4.** To stop the server, press `Ctrl+C` in the terminal.

> **Windows users:** Use `python` instead of `python3` if the above command is not found.

---

## Option C — Node.js Express Server

Use this option if you plan to extend ShadowGraph with a backend (SQLite database, API endpoints, authentication).

### Prerequisites

Install Node.js (version 18 or later):
- **macOS:** `brew install node` or download from [nodejs.org](https://nodejs.org)
- **Windows:** Download the LTS installer from [nodejs.org](https://nodejs.org)
- **Linux (Debian/Ubuntu):** `sudo apt install nodejs npm`

Verify installation:
```bash
node --version    # Should output v18.x.x or higher
npm --version     # Should output 9.x.x or higher
```

### Directory Setup

**Step 1.** Create the full project structure:

```bash
mkdir -p ~/shadowgraph/server
mkdir -p ~/shadowgraph/data
mkdir -p ~/shadowgraph/assets/fonts
mkdir -p ~/shadowgraph/docs
```

**Step 2.** Place your files in the correct locations:

```
~/shadowgraph/
├── shadowgraph.html          ← Copy here
├── README.md                 ← Copy here
├── QUICKSTART.md             ← Copy here
├── server/
│   ├── server.js             ← Create this (see Step 3)
│   └── package.json          ← Create this (see Step 4)
├── data/
│   └── (empty for now)
├── assets/
│   └── fonts/
│       └── (empty for now)
└── docs/
    └── (empty for now)
```

**Step 3.** Create `server/server.js`:

```bash
cat > ~/shadowgraph/server/server.js << 'EOF'
const express = require('express');
const path    = require('path');

const app  = express();
const PORT = process.env.PORT || 8080;

// Serve all files from the parent shadowgraph/ directory
const ROOT = path.join(__dirname, '..');
app.use(express.static(ROOT));

// Default route — serve the main app
app.get('/', (req, res) => {
  res.sendFile(path.join(ROOT, 'shadowgraph.html'));
});

app.listen(PORT, '127.0.0.1', () => {
  console.log(`\n╔══════════════════════════════════════╗`);
  console.log(`║  SHADOWGRAPH SERVER ONLINE           ║`);
  console.log(`║  http://localhost:${PORT}              ║`);
  console.log(`╚══════════════════════════════════════╝\n`);
});
EOF
```

**Step 4.** Create `server/package.json`:

```bash
cat > ~/shadowgraph/server/package.json << 'EOF'
{
  "name": "shadowgraph-server",
  "version": "1.0.0",
  "description": "ShadowGraph 6°NASA local server",
  "main": "server.js",
  "scripts": {
    "start":   "node server.js",
    "dev":     "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.18.0"
  },
  "devDependencies": {
    "nodemon": "^3.0.0"
  }
}
EOF
```

**Step 5.** Install dependencies:

```bash
cd ~/shadowgraph/server
npm install
```

Expected output:
```
added 65 packages in 3s
```

**Step 6.** Start the server:

```bash
npm start
```

**Step 7.** Open your browser:

```
http://localhost:8080
```

**Step 8 (optional).** For auto-reload during development (restarts server on file changes):

```bash
npm run dev
```

**Step 9.** To stop the server, press `Ctrl+C`.

---

## Option D — Fully Offline Mode

Use this when operating in an air-gapped environment or when CDN access is blocked.

This requires downloading and hosting the JavaScript libraries locally so the page never makes external requests.

### Step 1 — Complete Option C setup first

Follow all steps in Option C before continuing.

### Step 2 — Download library files

From a machine with internet access, download the following files:

```bash
cd ~/shadowgraph/assets

# Leaflet CSS
curl -o leaflet.min.css \
  https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css

# Leaflet JS
curl -o leaflet.min.js \
  https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js

# D3.js
curl -o d3.min.js \
  https://cdnjs.cloudflare.com/ajax/libs/d3/7.8.5/d3.min.js
```

Your `assets/` folder should now look like this:

```
assets/
├── leaflet.min.css
├── leaflet.min.js
└── d3.min.js
```

### Step 3 — Download offline map tiles (optional)

For fully air-gapped map tile serving you will need a local tile server. The simplest approach uses a pre-downloaded MBTiles file served by `tileserver-gl`.

```bash
# Install tileserver-gl globally
npm install -g tileserver-gl-light

# Download a tiles package (example: US region, ~500MB)
# Source: https://openmaptiles.org/downloads/
# Place the .mbtiles file in:
mkdir -p ~/shadowgraph/assets/tiles
# mv your-downloaded-file.mbtiles ~/shadowgraph/assets/tiles/map.mbtiles

# Start tile server on port 8081
tileserver-gl-light ~/shadowgraph/assets/tiles/map.mbtiles --port 8081
```

### Step 4 — Edit `shadowgraph.html` to use local assets

Open `shadowgraph.html` in a text editor and replace the CDN references:

**Find this section** (near the top of `<head>`):
```html
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.css"/>
```

**Replace with:**
```html
<link rel="stylesheet" href="/assets/leaflet.min.css"/>
```

**Find these script tags** (near the bottom of `<body>`):
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/7.8.5/d3.min.js"></script>
```

**Replace with:**
```html
<script src="/assets/leaflet.min.js"></script>
<script src="/assets/d3.min.js"></script>
```

**If using local tile server**, find the `L.tileLayer(...)` call in the JavaScript section and replace:
```javascript
// BEFORE — CartoDB CDN tiles
L.tileLayer('https://{s}.basemaps.cartocdn.com/dark_all/{z}/{x}/{y}{r}.png', {

// AFTER — Local tile server
L.tileLayer('http://localhost:8081/styles/dark-matter/{z}/{x}/{y}.png', {
```

**Remove the Google Fonts links** (lines 7–9) if offline fonts are needed. The tool will fall back to `Courier New` / `Trebuchet MS` automatically.

### Step 5 — Start all services

In separate terminal windows:

```bash
# Terminal 1 — Main app server
cd ~/shadowgraph/server && npm start

# Terminal 2 — Tile server (only if using local tiles)
tileserver-gl-light ~/shadowgraph/assets/tiles/map.mbtiles --port 8081
```

Navigate to `http://localhost:8080`.

---

## Final Directory Verification

Before launching, confirm your project directory matches this structure:

```
shadowgraph/
│
├── shadowgraph.html          ✓ Main application
├── README.md                 ✓ Documentation
├── QUICKSTART.md             ✓ This file
│
├── server/
│   ├── server.js             ✓ Express server
│   ├── package.json          ✓ npm manifest
│   ├── package-lock.json     ✓ Auto-generated after npm install
│   └── node_modules/         ✓ Auto-generated after npm install
│       └── (contents managed by npm — do not edit)
│
├── data/
│   ├── nodes.json            (optional — future external data)
│   └── edges.json            (optional — future external data)
│
├── assets/                   (only needed for offline mode)
│   ├── leaflet.min.css
│   ├── leaflet.min.js
│   ├── d3.min.js
│   ├── fonts/
│   │   └── (local .woff2 font files if needed)
│   └── tiles/
│       └── map.mbtiles       (optional offline tile package)
│
└── docs/
    └── (place ARCHITECTURE.md, DATA_SCHEMA.md here)
```

---

## Troubleshooting

### Map does not appear / blank center panel

**Cause:** Leaflet or D3 CDN assets failed to load.

**Fix:**
1. Open browser DevTools → Console (F12 or Cmd+Option+I)
2. Look for errors like `net::ERR_BLOCKED_BY_CLIENT` or `L is not defined`
3. If blocked: switch to Option D (offline mode) or disable ad blockers for localhost
4. Confirm internet connection is active

---

### `L is not defined` error in console

**Cause:** Leaflet JS script did not execute before the app initialized.

**Fix:** This is resolved in ShadowGraph v1.0 (uses `window.addEventListener('load')`). If you are seeing it, ensure you are using the latest `shadowgraph.html` (check the title tag reads `SHADOWGRAPH v1.0`).

---

### Clicking filters produces no visual change

**Cause:** Map not yet initialized (Leaflet still loading).

**Fix:** Wait for the map tiles to appear before clicking filters. On slow connections, Leaflet may take 3–5 seconds to fully initialize. The tool includes guards that prevent crashes during this window.

---

### `npm install` fails with permission errors (macOS/Linux)

**Fix:**
```bash
# Do NOT use sudo with npm. Instead, fix npm's global directory:
mkdir -p ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
npm install
```

---

### Port 8080 is already in use

**Fix:** Change the port in `server.js`:
```javascript
const PORT = process.env.PORT || 9090;   // Use any available port
```
Or pass it as an environment variable:
```bash
PORT=9090 npm start
```

---

### Map tiles are grey / not loading

**Cause:** CartoDB tile server (`basemaps.cartocdn.com`) requires internet access.

**Fix:** Use Option D (offline tiles) or connect to the internet.

---

### Windows-specific: `python3` not found

**Fix:** Try `python` instead:
```cmd
python -m http.server 8080
```
Or install Python from [python.org](https://www.python.org/downloads/) and ensure it is added to your system `PATH` during installation.

---

### Windows-specific: `curl` not found

**Fix:** Use PowerShell:
```powershell
Invoke-WebRequest -Uri "https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.9.4/leaflet.min.js" -OutFile "leaflet.min.js"
```

---

## Quick Reference — Commands

```bash
# Option B — Python server (simplest)
cd ~/shadowgraph && python3 -m http.server 8080

# Option C — Node.js server (install)
cd ~/shadowgraph/server && npm install

# Option C — Node.js server (run)
cd ~/shadowgraph/server && npm start

# Option C — Node.js server (dev mode with auto-reload)
cd ~/shadowgraph/server && npm run dev

# Option D — Tile server
tileserver-gl-light ~/shadowgraph/assets/tiles/map.mbtiles --port 8081

# Open in browser
open http://localhost:8080          # macOS
xdg-open http://localhost:8080      # Linux
start http://localhost:8080         # Windows
```

---

## Using the Tool — Quick UI Reference

| Control | Action |
|---|---|
| Click a subject in the left panel | Select node, fly map to location, open intel brief |
| Click a node marker on the map | Same as above |
| INTEL / TIMELINE / LINKS tabs | Switch right panel view for selected subject |
| ALL / DECEASED / MISSING buttons | Filter which node markers appear on map |
| WORK / ACQUAINTANCE / INSTITUTIONAL | Toggle connection line types on/off |
| MAP / GRAPH header buttons | Switch between geospatial map and force-directed graph |
| RESET button | Return map to default view, deselect all nodes |
| Click a connection in the Intel panel | Jump to that connected subject |
| Drag nodes (in GRAPH mode) | Reposition nodes in the force simulation |
| Scroll / pinch (in MAP mode) | Zoom in and out |

---

*SHADOWGRAPH // QUICKSTART // v1.0 // 2026-04-05*
