# Methodology

## Data Sources

This dataset is compiled from multiple open sources:

- **OpenDOSM** (CC BY 4.0) — Official Malaysian Department of Statistics open data portal providing the canonical 160-daerah list with DOSM state and district codes
- **geoBoundaries** (CC BY 4.0) — ADM1 (state), ADM2 (district), and ADM3 (mukim) polygon boundaries for centroid computation
- **OpenStreetMap Nominatim** — Geocoding for districts not matched in geoBoundaries

## Processing

1. State and district lists extracted from OpenDOSM population_district dataset
2. Mukim boundaries from geoBoundaries ADM3 (1,859 features)
3. Centroid coordinates computed from polygon geometry at all levels
4. Parent assignment for mukims via point-in-polygon spatial join against district polygons
5. Multi-format export: JSON, NDJSON, CSV
6. Hierarchy folder structure with READMEs generated via EJS templates

## Structure Notes

- **Peninsular Malaysia** has a 3-level hierarchy: State → District → Mukim
- **Sabah and Sarawak (East Malaysia)** do not use the mukim system; their ADM3 entries represent "Land Districts" instead
- **Federal Territories** (KL, Putrajaya, Labuan) are treated as state-level entities per ISO 3166-2:MY

## Code System

- State: ISO 3166-2:MY 2-digit suffix (01–16)
- District: sequential within state (assigned from DOSM ordering)
- Mukim: `{district_id}-{nnn}` (spatial assignment)

## Accuracy

- All division names from DOSM official census data
- Coordinates: 100% at all levels (polygon centroids)
- Mukim-to-district assignment: 98% via spatial join, 2% via nearest-neighbour fallback
- Build script is idempotent: same input always produces same output