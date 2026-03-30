# South London Post

An open ontology and content aggregator for places in South London.

## What this is

South London Post is a two-part project:

1. **A place ontology** — a structured, four-level hierarchy of South London place names (Region → Borough → Neighbourhood → Landmark/Street), cross-referenced to authoritative public sources and published as linked open data.
2. **A content aggregator prototype** — a browsable web application that surfaces fresh local content (news, events, council notices) organised by place, ranked by source credibility.

## Borough scope

This project covers the **five statutory Inner London boroughs south of the River Thames**, as defined by Schedule 1 of the [London Government Act 1963 (c.33)](https://www.legislation.gov.uk/ukpga/1963/33/schedule/1):

| Borough | ONS Code |
|---|---|
| London Borough of Lambeth | E09000022 |
| London Borough of Southwark | E09000028 |
| London Borough of Lewisham | E09000023 |
| London Borough of Wandsworth | E09000032 |
| Royal Borough of Greenwich | E09000011 |

The inclusion rule is: **a borough is included if and only if it is (a) a statutory Inner London borough under the 1963 Act, and (b) south of the River Thames**. See [`docs/borough-inclusion-rule.md`](docs/borough-inclusion-rule.md) for the full rationale and alternatives considered.

## Repository structure

```
southlondonpost/
├── ontology/                  # Place ontology (JSON-LD)
│   └── south-london-ontology.jsonld
├── app/                       # Prototype web application
│   └── index.html
├── docs/                      # Supporting documentation
│   ├── borough-inclusion-rule.md
│   ├── ontology-guide.md
│   ├── sources.md
│   └── prominence-scoring.md
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── place-addition.md
│       └── data-correction.md
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

## Ontology

The ontology is published as [JSON-LD](https://json-ld.org/), using vocabularies from [schema.org](https://schema.org/), [SKOS](https://www.w3.org/2004/02/skos/core), and [Dublin Core](https://www.dublincore.org/). Every place node carries:

- A stable `@id` URI
- `sameAs` links to Wikidata, OpenStreetMap, and Wikipedia equivalents
- ONS geography codes where applicable
- Governing body (council) references
- Postal districts and TfL zones
- Source attribution for all properties

See [`docs/ontology-guide.md`](docs/ontology-guide.md) for a full property reference.

## Data sources

| Source | Used for | Licence |
|---|---|---|
| ONS / OS | Borough boundaries, ONS codes, ward boundaries | Open Government Licence v3.0 |
| OpenStreetMap | Neighbourhood boundaries, landmark geometries, aliases | ODbL 1.0 |
| Wikidata | Cross-references, `sameAs` links, aliases | CC0 1.0 |
| TfL Open Data | TfL zones, station references | TfL Open Data Licence |
| Royal Mail PAF | Postal districts (indicative only) | Commercial — reference only |

## Licence

The ontology and documentation in this repository are published under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

Note that data derived from OpenStreetMap carries an additional share-alike obligation under the [Open Database Licence (ODbL)](https://opendatacommons.org/licenses/odbl/). See [`docs/sources.md`](docs/sources.md) for full licence details per source.

## Contributing

Contributions are welcome — particularly additions to the place hierarchy, corrections to ONS/OSM cross-references, and new source attributions. Please read [`CONTRIBUTING.md`](CONTRIBUTING.md) before submitting a pull request.

## Status

**Prototype — v0.2.0.** The ontology covers five boroughs with selected neighbourhoods and landmarks. Full neighbourhood and landmark coverage is in progress.

## Citation

If you use this ontology in research or a derived project, please cite it as:

> South London Post (2025). *South London Place Ontology*, v0.2.0. GitHub. https://github.com/lloydshep/southlondonpost

A Zenodo DOI for formal academic citation will be registered at v1.0.0.

## Acknowledgements

This project was researched and structured with assistance from [Claude](https://www.anthropic.com) (Anthropic). Claude contributed to the ontology design, schema authoring, documentation drafting, and borough inclusion research. All source attributions, legislative citations, and place data have been independently verified by the project author.

This is noted in machine-readable form in the `_meta.provenance` field of the ontology JSON-LD file.
