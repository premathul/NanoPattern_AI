# Contributing to NanoPattern AI

NanoPattern AI is an early research-software project for nanofabrication design and verification.

## Development principles

1. Geometry and DRC calculations must be deterministic and independently testable.
2. AI-generated design changes must be represented as explicit operations before execution.
3. Units must be explicit; the current design workspace uses nanometres internally.
4. Fabrication claims must distinguish heuristic guidance from calibrated process rules.
5. New scientific features should include validation examples and numerical tests.

## Current development

The public v0.3 application is a standalone browser prototype in `index.html`. Future work is being organized into `frontend/`, `backend/`, `geometry/`, `drc/`, and `docs/`.
