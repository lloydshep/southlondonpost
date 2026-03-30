# Data sources and licences

This document records every external data source used in the South London Post ontology, the properties each source underpins, and the licence obligations that apply.

## Source summary

| Source | Properties | Licence | Obligations |
|---|---|---|---|
| ONS / OS | `onsCode`, ward codes, borough boundaries | OGL v3.0 | Attribution required |
| Ordnance Survey | Boundary geometries, UPRN references | OS Open Data Licence | Attribution required |
| OpenStreetMap | `osmId`, neighbourhood boundaries, landmark geometries, `alternateName` | ODbL 1.0 | Attribution + share-alike on derived databases |
| Wikidata | `sameAs` links, `wikidataId`, aliases | CC0 1.0 | None |
| TfL Open Data | `tflZones`, station references | TfL Open Data Licence | Attribution required |
| Royal Mail PAF | `postalDistricts` (indicative only) | Commercial | Reference only — not redistributed |
| Wikipedia | Human-readable descriptions, `sameAs` links | CC BY-SA 3.0 | Attribution + share-alike for derived prose |

## Detailed source records

### Office for National Statistics (ONS)

- **Base URL:** https://statistics.data.gov.uk/
- **Licence:** [Open Government Licence v3.0](https://www.nationalarchives.gov.uk/doc/open-government-licence/)
- **Used for:** `onsCode` (statistical geography codes), ward boundary codes, borough boundary definitions
- **Attribution:** Contains public sector information licensed under the Open Government Licence v3.0.

### Ordnance Survey (OS)

- **Base URL:** https://osdatahub.os.uk/
- **Products:** OS Boundary-Line, OS AddressBase
- **Licence:** [OS Open Data Licence](https://www.ordnancesurvey.co.uk/documents/licensing/data-licence.pdf)
- **Used for:** Official boundary geometries, UPRN references
- **Attribution:** Contains OS data © Crown copyright and database right 2024.

### OpenStreetMap (OSM)

- **Base URL:** https://www.openstreetmap.org/
- **Licence:** [Open Database Licence (ODbL) 1.0](https://opendatacommons.org/licenses/odbl/)
- **Used for:** `osmId`, neighbourhood and landmark boundary geometries, `alternateName` values
- **Attribution:** © OpenStreetMap contributors
- **Share-alike obligation:** Any database derived from OSM data must be published under the ODbL. This ontology as a whole is therefore subject to ODbL share-alike in addition to its CC BY 4.0 licence, where OSM-derived properties are included.

### Wikidata

- **Base URL:** https://www.wikidata.org/
- **Licence:** [Creative Commons CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)
- **Used for:** `sameAs` URIs, `wikidataId`, cross-referencing, alias verification
- **Obligations:** None — CC0 places data in the public domain.

### Transport for London (TfL) Open Data

- **Base URL:** https://api.tfl.gov.uk/
- **Licence:** [TfL Open Data Licence](https://tfl.gov.uk/corporate/terms-and-conditions/transport-data-service)
- **Used for:** `tflZones`, underground and rail station references
- **Attribution:** Powered by TfL Open Data.

### Royal Mail Postcode Address File (PAF)

- **Base URL:** https://www.royalmail.com/business/data
- **Licence:** Commercial
- **Used for:** `postalDistricts` values (indicative only — postal districts are listed as reference metadata and are not redistributed as a dataset)
- **Note:** Postal district values are derived from common knowledge and cross-checked against PAF; the PAF itself is not reproduced.

### Wikipedia

- **Base URL:** https://en.wikipedia.org/
- **Licence:** [Creative Commons Attribution-ShareAlike 3.0](https://creativecommons.org/licenses/by-sa/3.0/)
- **Used for:** `sameAs` links to Wikipedia articles; human-readable descriptions where quoted
- **Note:** Wikipedia article URLs are used as `sameAs` identifiers only; no Wikipedia prose is reproduced in the ontology.

## Combined licence obligations

Users of this ontology should be aware of the following stacked obligations:

1. **Attribution** is required for ONS, OS, TfL, and OSM data.
2. **Share-alike** applies to any derived database that incorporates OSM-derived properties (ODbL).
3. The project licence (CC BY 4.0) applies to the ontology structure, documentation, and non-OSM-derived content.

If you are building a derived product, the safest approach is to publish your derived data under ODbL and provide attribution to all sources listed above.
