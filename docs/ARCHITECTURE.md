# NanoPattern AI Architecture

NanoPattern AI is being developed as a nanofabrication CAD, verification, and AI-assisted design platform.

## Current architecture

The v0.3 application is intentionally self-contained in `index.html`. It runs entirely in the browser and contains:

- parametric nanobeam and periodic-array generation;
- deterministic feature spacing and overlap calculations;
- configurable minimum-feature, minimum-gap, and taper-step checks;
- interactive SVG visualization;
- CSV import/export and SVG export;
- an offline design copilot that converts supported natural-language instructions into parameter operations.

The copilot does **not** perform the final geometry arithmetic. Geometry is recalculated by deterministic code after every operation.

## Target architecture

```text
Browser / Desktop UI
        |
        v
Design command layer
        |
        +----> AI tool router
        |
        v
Deterministic geometry kernel
        |
        +----> DRC engine
        +----> GDSII / OASIS I/O
        +----> parametric device library
        +----> optimization engine
        |
        v
Verified layout + fabrication report
```

### Frontend

The production frontend should eventually move to React/Next.js or an equivalent component architecture while preserving the CAD-style workspace.

### Backend

A Python/FastAPI backend will provide server-side AI calls, project persistence, job execution, private file storage, and interfaces to scientific/nanofabrication libraries.

### Geometry

Planned geometry dependencies:

- KLayout for mature GDS/OASIS and DRC workflows;
- gdstk for programmatic GDSII construction;
- Shapely for polygon operations;
- NumPy/SciPy for numerical geometry and optimization.

### DRC

The DRC engine must remain deterministic. AI can propose changes, explain failures, and generate tool commands, but it must not be the source of truth for dimensional signoff.

### Security

No production API keys should be embedded in browser JavaScript. Unpublished device layouts should support private storage or local-only execution.
