# Travel Pulse performance follow-up

This is a conservative patch, **not** a completed precomputation overhaul.

- World map load now schedules active-tab rendering for Airline, Hotel and Travel Behaviour as well as the existing map tabs.
- Removed an unconditional second 3D airline-map render 120 ms after the first.
- Retained original world.geojson and existing calculations, source datasets, charts and filters.
- Existing data/precomputed/ summaries and scripts/precompute_dashboard.py were inspected and left unchanged; they already cover several survey questions but do not replace every map/brand computation.

Run: `python -m http.server 8000` in this folder. Recompute survey summaries only when source data changes: `python scripts/precompute_dashboard.py`.

Validation: JS syntax and ZIP integrity only. Browser benchmarking, regression tests and end-to-end precomputation are not complete.
