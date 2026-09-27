# NanoPattern AI — v0.3

A browser-based nanofabrication design and verification workspace focused on EBL nanostructures.

## Current v0.3 highlights

- Professional graphite scientific-CAD interface with a restrained blue accent and fabrication-status colors reserved for warnings and violations.
- Added a richer device viewer with region labels, overview/minimap, CAD and SEM-style views, optional dimensions, hover details, and live design HUD.
- Reworked NanoPattern Copilot so it actually executes a useful set of local design commands.
- Added Enter-to-send and quick command chips.
- Added deterministic auto-repair for minimum edge-gap violations.
- Added taper-smoothing logic.
- Added design explanation and failure-diagnosis responses.
- Added SVG export in addition to CSV.
- Added live design-health score and process-rule verification.

## Copilot commands that work offline

Examples:

- `make minimum gap 120 nm`
- `set cavity diameter to 230 nm`
- `set mirror diameter to 250 nm`
- `set mirror pitch to 600 nm`
- `set taper holes to 7`
- `fix all DRC failures`
- `optimize taper smoothness`
- `explain the current design`
- `why is the design failing?`
- `reset to demo`

The copilot does not perform geometry arithmetic itself. It converts supported natural-language requests into parameter operations; the deterministic geometry engine recomputes spacing, overlap, symmetry, feature-size rules and taper continuity.

## Important distinction: offline copilot vs. cloud LLM

This single HTML file has no secret API key and therefore does **not** call ChatGPT or another external model. That is intentional: putting an API key directly inside browser JavaScript would expose it to every user.

A production version should use:

- Frontend: React / Next.js
- Backend: Python / FastAPI
- LLM calls: server-side only
- Layout processing: gdstk + KLayout
- Geometry: Shapely / NumPy
- Optimization: SciPy / Optuna
- Storage: PostgreSQL + private object storage
- Optional local worker for unpublished device layouts

## Run

Open `index.html` directly in Chrome, Edge, Safari, or Firefox. No installation is required.

Or serve locally:

```bash
python3 -m http.server 8000
```

then open `http://localhost:8000`.

## Scientific scope

This prototype is a design aid. It is not yet a calibrated foundry DRC engine, proximity-effect correction package, or fabrication signoff tool. Real GDSII/OASIS import/export and KLayout rule-deck integration are the next major engineering milestone.
