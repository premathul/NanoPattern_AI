# Design Rule Checking

NanoPattern AI treats DRC as deterministic engineering logic, not an LLM task.

The current browser prototype checks:

- minimum feature diameter;
- minimum adjacent edge gap;
- feature overlap;
- mirror symmetry;
- taper diameter-step preference.

The production DRC system should support configurable process rule decks, polygon-level width/spacing rules, enclosure and separation constraints, layer-specific checks, and KLayout-compatible rule execution.
