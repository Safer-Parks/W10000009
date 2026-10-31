# Safer Parks data: `South Wales West` (`W10000009`)

Regional dataset for the [Safer Parks Dashboard](https://safer-parks.github.io/), covering parks in South Wales West (England/Wales). The data in this repository is loaded directly by the dashboard from `https://raw.githubusercontent.com/Safer-Parks/W10000009/refs/heads/main`.

## Citation

> Francesca Pontin, Anna Barker, Melissa Barrientos, Victoria Houlden, Maeve Murphy Quinlan (2026): The Safer Parks Dashboard Data: South Wales West, (Version V0.1.0). University of Leeds. DOI HERE. Accessed: *Insert today's date*.

| Field | Value |
|------------------------------------|------------------------------------|
| DOI | `[DOI – pending Zenodo release]` |
| Version | V0.1.0 |
| Release date | 01-11-2026 |
| Authors / creators | Francesca Pontin, Anna Barker, Melissa Barrientos, Victoria Houlden, Maeve Murphy Quinlan |
| Dashboard | [Safer Parks Dashboard landing page](https://safer-parks.github.io/) |

When using this data, please also acknowledge the underlying data sources and licences listed below.

## Licence

Copyright 2026 University of Leeds.

This dataset contains material under different licences:

Source code: the code for the Safer Parks Dashboard and its data-processing scripts is licensed under the MIT Licence: The MIT License – Open Source Initiative. The full licence text is provided in the LICENSE file included with the code.

Other content: unless otherwise stated, all other content created by the authors, including documentation, text, figures, screenshots and outputs or insights derived from the dashboard, is licensed under a Creative Commons Attribution-ShareAlike 4.0 International Licence (CC BY-SA 4.0): https://creativecommons.org/licenses/by-sa/4.0/

Third-party data: third-party data included in this dataset, displayed in the dashboard, or used to derive it (including any basemap imagery shown in screenshots) remain subject to their original licences and attribution requirements (see Section 5). The licences above do not apply to this material.

For further details, please see our [citation page](https://safer-parks.github.io/).

| Item | Details |
|------------------------------------|------------------------------------|
| Licence for Safer Parks derived data | Creative Commons Attribution-ShareAlike 4.0 International Licence (CC BY-SA 4.0): https://creativecommons.org/licenses/by-sa/4.0/ |
| Licences of underlying sources | See [Data sources and licences](#data-sources-and-licences); source licence terms continue to apply. |

## Repository structure

All data are GeoJSON (`.geojson`). `[AUTHORITY_ID]` is the local authority code and `[AUTHORITY_NAME]` the authority name; `[PARK_ID]` is the park's official ID and `[NEW_PARK_ID]` the park's Safer Parks ID.

```         
W10000009_lut.geojson                      region look-up table (authorities and parks)
[AUTHORITY_ID]/
  [AUTHORITY_NAME]_parks.geojson               } park boundaries (the dashboard tries these
  [AUTHORITY_NAME]_pocket_parks.geojson        } three names in this order and loads
  [AUTHORITY_NAME]_pp_or_g_cmb.geojson         } the first one found)
  [AUTHORITY_NAME]_park_entrances.geojson
  [AUTHORITY_NAME]_features_within_pp_or_g.geojson
  [AUTHORITY_NAME]_features_not_in_pp_or_g.geojson
  [AUTHORITY_NAME]_street_lamps.geojson
  [AUTHORITY_NAME]_national_cycle_network.geojson
  [AUTHORITY_NAME]_pp_or_g_cmb/
    [NEW_PARK_ID]_visibility.geojson
    [NEW_PARK_ID]_foliage.geojson
  NACH_dataset/[PARK_ID]_NACH.geojson
  toilet_dataset/[PARK_ID]_toilets.geojson
  bench_dataset/[PARK_ID].geojson
  cycling_dataset/[PARK_ID]_cycling.geojson
  walking_dataset/[PARK_ID]_walking.geojson
  lighting_supplemented/[PARK_ID]_lighting.geojson
  lighting_supplemented/[PARK_ID]_lighting_buffer.geojson
  demo/[AUTHORITY_NAME]_15_min.geojson
```

## Data files loaded by the dashboard

Scale: **Region** = one file for the region; **Authority** = one file per local authority; **Park** = one file per park. Not every file exists for every authority or park (e.g. toilets, walking routes and supplemental lighting are not yet available everywhere).

| \# | Dashboard layer | File (pattern) | Format | Scale | Geometry | Displayed as |
|-----------|-----------|-----------|-----------|-----------|-----------|-----------|
| 1 | Region look-up table | `W10000009_lut.geojson` | GeoJSON | Region | `[GEOMETRY]` | Authority and park selection lists |
| 2 | Park Boundary / Nearby Parks | `[AUTHORITY_NAME]_parks.geojson`, or `_pocket_parks.geojson`, or `_pp_or_g_cmb.geojson` | GeoJSON | Authority | Polygon | Polygon |
| 3 | Pocket Parks (\< 5000 m²) | `[AUTHORITY_NAME]_pocket_parks.geojson` | GeoJSON | Authority | Polygon | Polygon |
| 4 | Access and Exit Points | `[AUTHORITY_NAME]_park_entrances.geojson` | GeoJSON | Authority | Point | Points |
| 5 | Features and facilities (within parks) | `[AUTHORITY_NAME]_features_within_pp_or_g.geojson` | GeoJSON | Authority | `[GEOMETRY]` | Points/polygons |
| 6 | Features and facilities (nearby, not in parks) | `[AUTHORITY_NAME]_features_not_in_pp_or_g.geojson` | GeoJSON | Authority | `[GEOMETRY]` | Points/polygons |
| 7 | Visibility Analysis | `[AUTHORITY_NAME]_pp_or_g_cmb/[NEW_PARK_ID]_visibility.geojson` | GeoJSON | Park | Polygon (hexagon grid) | Hexagonal grid, dark (low) to bright (high) |
| 8 | Low Foliage (\< 0.5 m), Mid Foliage (0.5–2 m), Tall Foliage (2 m+) | `[AUTHORITY_NAME]_pp_or_g_cmb/[NEW_PARK_ID]_foliage.geojson` | GeoJSON | Park | Polygon (hexagon grid) | Hexagonal grid (one layer per height band) |
| 9 | Predicted Route Popularity (NACH) | `NACH_dataset/[PARK_ID]_NACH.geojson` | GeoJSON | Park | Line | Line network |
| 10 | Toilet Facilities | `toilet_dataset/[PARK_ID]_toilets.geojson` | GeoJSON | Park | Point | Icons with details popup (incl. accessibility) |
| 11 | Benches & Picnic Tables | `bench_dataset/[PARK_ID].geojson` | GeoJSON | Park | Point | Points |
| 12 | Cycling Routes | `cycling_dataset/[PARK_ID]_cycling.geojson` | GeoJSON | Park | Line | Lines |
| 13 | Walking Routes | `walking_dataset/[PARK_ID]_walking.geojson` | GeoJSON | Park | Line | Lines |
| 14 | Supplemental Lighting | `lighting_supplemented/[PARK_ID]_lighting.geojson` | GeoJSON | Park | Point | Points |
| 15 | Supplemental Lighting (200 m buffer) | `lighting_supplemented/[PARK_ID]_lighting_buffer.geojson` | GeoJSON | Park | Polygon | Buffer outline |
| 16 | Demographics (15 min walking catchment) | `demo/[AUTHORITY_NAME]_15_min.geojson` | GeoJSON | Authority | Polygon | Polygon with popup (LQ values) |
| 17 | National Cycling Network | `[AUTHORITY_NAME]_national_cycle_network.geojson` | GeoJSON | Authority | Line | Lines |
| 18 | Coloured Basemap | Not stored in this repository; loaded from OpenStreetMap tiles | Map tiles | – |  Raster| Grayscale or full-colour basemap |

## Data sources and licences {#data-sources-and-licences}

| Dashboard layer | What the layer is | Source(s) | Licence | Attribution / notes |
|---------------|---------------|---------------|---------------|---------------|
| Coloured Basemap | Schematic background map showing roads, buildings, green spaces and water. Not analytical; provides spatial context. | OpenStreetMap | [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright){target="_blank"} |
| National Cycling Network | Cycling and walking infrastructure within and around parks, displayed as lines. | OpenStreetMap, downloaded via Geofabrik and filtered to extract active travel infrastructure across England and Wales. | [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | Split into two layers: **cycling** (cycleways, cycle lanes, shared paths, bridleways, tracks) and **walking** (footways, pedestrian areas, shared paths, bridleways, tracks). Shared paths, bridleways and tracks appear in both. |
| Pocket Parks | Green spaces smaller than 5000 m². | Combined Ordnance Survey and OpenStreetMap greenspace datasets. | OS Open Greenspace: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"};<br> OSM: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | Parks and formal gardens identified using the classifications: Public Park or Garden (Ordnance Survey), Park (OpenStreetMap), Garden (OpenStreetMap). |
| Park Boundary | Boundary of each park, displayed as a polygon; the spatial reference for all other layers. | Combined Ordnance Survey and OpenStreetMap greenspace datasets. | OS Open Greenspace: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"};<br> OSM: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | Same classifications as Pocket Parks. |
| Nearby Parks | Other parks within the same local authority area. Not analytical; used to navigate between parks. | Combined Ordnance Survey and OpenStreetMap greenspace datasets. | OS Open Greenspace: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"};<br> OSM: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | – |
| Access and Exit Points | Locations of external park entrances, displayed as points. | Ordnance Survey and OpenStreetMap (primary entrances); calculated secondary entry points. | OS Open Greenspace: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"};<br> OSM: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | Distinguishes **primary** entrances (as mapped by OS and OSM) from **secondary/additional** entry points, calculated where a footpath intersects the Park Boundary. |
| Features and facilities | Features within parks and nearby. For the selected park, shows features whose mapped extents intersect the park boundary or an 800 m buffer around it. | Combined Ordnance Survey and OpenStreetMap data. | OS Open Greenspace: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"};<br> OSM: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | The buffer is applied as an expanded bounding box, so features near the corners may be slightly further than 800 m away. |
| Visibility Analysis | How visually connected different parts of the park are (considers elevation, tree canopy height, shrub height), displayed as a hexagonal grid. | DEFRA LiDAR and author-generated analysis. England: 2022 composite dataset (Digital Surface Model and Digital Terrain Model). Wales: 32-bit LiDAR dataset. | DEFRA LiDAR: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"} derived analysis: <br> see note above on derived data license. | Method: https://github.com/Safer-Parks/park-vga and https://github.com/Safer-Parks/park-vga/blob/main/notebooks/finding_lidar_tiles/README_downloading.md |
| Low Foliage (\< 0.5 m) | Vegetation coverage below 0.5 m, shown as a hexagonal grid. | DEFRA LiDAR (elevation, tree canopy height, shrub height). England: 2022 composite DSM/DTM. Wales: 32-bit LiDAR. | DEFRA LiDAR: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"} derived analysis: <br> see note above on derived data license. | Calculated from LiDAR scans, so it also captures buildings and other structures that are not vegetation. Represents a "worst case" visibility scenario (full summer leaf coverage). Method: https://github.com/Safer-Parks/park-vga |
| Mid Foliage (0.5–2 m) | Vegetation coverage between 0.5 and 2 m, shown as a hexagonal grid. | DEFRA LiDAR (elevation, tree canopy height, shrub height). England: 2022 composite DSM/DTM. Wales: 32-bit LiDAR. | DEFRA LiDAR: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"} derived analysis: <br> see note above on derived data license. | Calculated from LiDAR scans, so it also captures buildings and other structures that are not vegetation. Represents a "worst case" visibility scenario (full summer leaf coverage). Method: https://github.com/Safer-Parks/park-vga |
| Tall Foliage (2 m+) | Vegetation coverage above 2 m, shown as a hexagonal grid. Hovering shows the vegetation height in each hexagon. | DEFRA LiDAR (elevation, tree canopy height, shrub height). England: 2022 composite DSM/DTM. Wales: 32-bit LiDAR. | DEFRA LiDAR: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"} derived analysis: <br> see note above on derived data license. | Calculated from LiDAR scans, so it also captures buildings and other structures that are not vegetation. Represents a "worst case" visibility scenario (full summer leaf coverage). Method: https://github.com/Safer-Parks/park-vga |
| Predicted Route Popularity (NACH) | Likely pedestrian movement through streets and paths at neighbourhood scale (\~10-minute walk); higher values indicate greater potential footfall and co-presence. Displayed as a line network. | Space Syntax (University College London, UCL) analysis using Normalised Angular Choice (NACH) at 800 m (approx. 10-minute walk), derived from OpenStreetMap street network data. | Street network: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"}; derived analysis: <br> see note above on derived data license. | Layer is in active development and testing. |
| Toilet Facilities | Toilets within a 15-minute walk of the park, with details including accessibility information. | [Toilet Map](https://www.toiletmap.org.uk/dataset) – https://www.toiletmap.org.uk/ | [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.en){target="_blank" aria-label="Link to CC BY 4.0 Attribution guidance"} | © 2025 Toilet Map. No changes made to the data, other than spatially filtering to toilets within 800m of the park. |
| Benches & Picnic Tables | Location of seating within parks, displayed as points. | Ordnance Survey and OpenStreetMap. | OS Open Greenspace: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information (opens in a new tab)"}; OSM: [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"}; | – |
| Cycling Routes | Cycling infrastructure within and around parks, displayed as lines. | OpenStreetMap via Geofabrik (see National Cycling Network). | [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | Cycling layer: cycleways, cycle lanes, shared paths, bridleways, tracks. |
| Walking Routes | Walking infrastructure within and around parks, displayed as lines. | OpenStreetMap via Geofabrik (see National Cycling Network). | [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/){target="_blank" aria-label="Link to Open Data Commons Open Database License (ODbL) v1.0 (opens in a new tab)"} | Walking layer: footways, pedestrian areas, shared paths, bridleways, tracks. |
| Supplemental Lighting | Locations of street lighting within and around parks, cut to a 200 m buffer around the park; displayed as points. | Data provided by local authorities: `\[LOCAL_AUTHORITY_NAMES\]`. | `\[LICENCE / TERMS FROM LOCAL AUTHORITY\]` | May not capture all assets. Verify with local authority records and on-the-ground knowledge. |
| Demographics (15 min walking catchment) | Demographic profile of people within a 15-minute walk of park access/exit points, displayed as a polygon. Variables: health, economic activity, ethnicity, country of origin, religion, household deprivation. | Census Output Area data: `\[CENSUS_SOURCE – e.g. ONS Census 2021\]`; street/path network for isochrones: OpenStreetMap. | Census: [OGL v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/){target="_blank" aria-label="Link to Open Government Licence for public sector information  (opens in a new tab)"}; derived catchments: <br> see above note for derived datasets. | See methodology below. |

### Demographics methodology

| Item | Details |
|------------------------------------|------------------------------------|
| Parks included | Parks of 10 hectares or larger (aligned with the Green Infrastructure Framework). |
| Catchment | 15-minute walking isochrone (4 km/h) from every identified park access and exit point, using the street and path network. This is effectively the reverse of the DEFRA Access to Greenspace methodology, which calculates accessibility from neighbourhoods to the nearest greenspace. |
| Population unit | Census Output Areas (OAs), generally 40–250 households and 100–625 residents (rural OAs are much larger in physical size). OAs with at least 20% of their area inside the catchment are included. |
| Comparison | Location quotient (LQ): relative concentration of a demographic group in the park catchment compared with the whole local authority. |
| Formula | `LQ = (Parkdem / Parkpop) / (LAdem / LApop)` |
| `Parkdem` | Count of the demographic group in the park catchment area |
| `Parkpop` | Total population of the park catchment area |
| `LAdem` | Count of the demographic group within the local authority |
| `LApop` | Total population within the local authority |
| Interpretation | `[LQ INTERPRETATION AND DEMOGRAPHIC DATA SOURCE INFO]` |
| Display | The popup shows the LQ and a symbol indicating how the catchment differs from the local authority. |

## Region details

| Field                       | Value                                        |
|------------------------------------|------------------------------------|
| Region name                 | South Wales West                              |
| Region code                 | W10000009                              |
| Local authorities included  | Bridgend, Neath Port Talbot, Swansea                      |
| Coordinate reference system | EPSG:4326 unless otherwise stated in dataset |
| Date data last updated      | 01-11-2026                        |

## Disclaimer

Data may not capture all assets (e.g. lighting) and some layers are in active development. Verify with local authority records and on-the-ground knowledge.

### Dashboard project warranty and liability

The software is provided “as is”, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.

© University of Leeds, 2026.
