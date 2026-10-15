# Performance optimization notes

## Changes applied
- Simplified world map topology at 0.012-degree tolerance while preserving country names, ISO codes, and topology. Original `world.geojson` is retained; app loads `world-optimized.geojson`. This reduces map download, JSON parsing, and SVG rendering cost. Some fine coastline detail is intentionally reduced.
- Moved background row-level record loading to the browser idle callback with a 1.5-second maximum delay (250 ms fallback), so the initial interface has time to render first.
- Prevented world-map fetch from triggering a redundant render on tabs that do not show country maps.
- Fixed rejected chunk promises remaining cached, allowing retry on later calls.

## Already present in uploaded project
- Precomputed summaries and filter options in `data/precomputed/`.
- Lazy matrix and social data loading.
- Regional record chunks and bootstrap data.

## Running
Run `python -m http.server 8000` from the project root and visit http://localhost:8000.
When source survey data changes, run `python scripts/precompute_dashboard.py` after regenerating normalized record chunks.

## Validation limits
JavaScript syntax and JSON parsing verified. Actual browser load timing and interactive chart regression testing require a real browser and were not completed here.


MAP REGRESSION FIX: Reverted the world geometry to the original world.geojson and removed the simplified world-optimized.geojson. Other optimizations are unchanged. Clear browser cache before testing.
