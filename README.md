# Malaysia Administrative Divisions / Malaysia

Open dataset of Malaysia's administrative hierarchy — from states (negeri) through districts (daerah) down to subdistricts (mukim). This repository provides structured reference data for all three levels of Malaysian administrative divisions, including geographic coordinates. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| State | 16 |
| District | 160 |
| Subdistrict | 1,859 |
| Coordinates | ✅ Included (all levels) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-06-01 |
| Website | [openadmindata.org/my](https://openadmindata.org/my/) |
| API | [openadmindata.org/api/my](https://openadmindata.org/api/my/) |

## Browse by State

| # | State | Districts | Subdistricts | Link |
|---|----|----|----|------|
| 1 | Johor | 10 | 95 | [Browse](divisions/johor-01/) |
| 2 | Kedah | 12 | 212 | [Browse](divisions/kedah-02/) |
| 3 | Kelantan | 11 | 302 | [Browse](divisions/kelantan-03/) |
| 4 | Melaka (Malacca) | 3 | 107 | [Browse](divisions/malacca-04/) |
| 5 | Negeri Sembilan | 7 | 154 | [Browse](divisions/negeri-sembilan-05/) |
| 6 | Pahang | 11 | 128 | [Browse](divisions/pahang-06/) |
| 7 | Pulau Pinang (Penang) | 5 | 47 | [Browse](divisions/penang-07/) |
| 8 | Perak | 13 | 185 | [Browse](divisions/perak-08/) |
| 9 | Perlis | 1 | 23 | [Browse](divisions/perlis-09/) |
| 10 | Selangor | 9 | 212 | [Browse](divisions/selangor-10/) |
| 11 | Terengganu | 8 | 96 | [Browse](divisions/terengganu-11/) |
| 12 | Sabah | 27 | 0 | [Browse](divisions/sabah-12/) |
| 13 | Sarawak | 40 | 285 | [Browse](divisions/sarawak-13/) |
| 14 | W.P. Kuala Lumpur (Federal Territory of Kuala Lumpur) | 1 | 12 | [Browse](divisions/federal-territory-of-kuala-lumpur-14/) |
| 15 | W.P. Labuan (Federal Territory of Labuan) | 1 | 1 | [Browse](divisions/federal-territory-of-labuan-15/) |
| 16 | W.P. Putrajaya (Federal Territory of Putrajaya) | 1 | 0 | [Browse](divisions/federal-territory-of-putrajaya-16/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-state.json](data/all-state.json) | JSON | All 16 state records |
| [all-district.json](data/all-district.json) | JSON | All 160 district records |
| [all-mukim.json](data/all-mukim.json) | JSON | All 1,859 subdistrict records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-2 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-state.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-state.json", "utf-8"));
console.log(`Total: ${data.length} states`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=state, 2=district, 3=subdistrict |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{state-slug}/
divisions/{state-slug}/{district-slug}/
```

Subdistricts are listed inline in each district's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-state links
- [Per-state data](docs/llms-full/) — Full data by state

## Citation

```
Malaysia Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/malaysia-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [Open Admin Data](https://openadmindata.org) — Browse, search and explore administrative divisions for every country
- [open-admin-data](https://github.com/open-admin-data) — GitHub organization with all country repos
- [ListBase](https://www.listbase.org) — Structured reference data for every country
