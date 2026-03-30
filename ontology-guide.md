# Ontology guide

## Overview

The South London Post place ontology is a four-level hierarchy of named places, published as [JSON-LD](https://json-ld.org/) linked open data. It is designed to be both human-readable and machine-consumable, and is cross-referenced to authoritative public sources at every level.

## Place levels

| Level | Definition | Example |
|---|---|---|
| Region | The overall service area — South London as a whole | South London |
| Borough | A statutory Inner London borough (London Government Act 1963) | London Borough of Lambeth |
| Neighbourhood | A commonly recognised sub-area within a borough | Brixton |
| Landmark / Street / Site | A specific named place, street, market, park or institution | Brixton Market |

Neighbourhood boundaries follow OpenStreetMap administrative relations where available, supplemented by common usage. They may or may not align with electoral ward boundaries.

## Vocabularies used

| Prefix | Vocabulary | URI |
|---|---|---|
| `schema:` | schema.org | https://schema.org/ |
| `skos:` | W3C SKOS | http://www.w3.org/2004/02/skos/core# |
| `dcterms:` | Dublin Core Terms | http://purl.org/dc/terms/ |
| `ons:` | ONS statistical geography | http://statistics.data.gov.uk/def/statistical-geography# |
| `os:` | OS AdminGeo | http://data.ordnancesurvey.co.uk/ontology/admingeo/ |
| `osm:` | OpenStreetMap | https://www.openstreetmap.org/ |

## Properties reference

### Properties on all nodes

| Property | Type | Source | Description |
|---|---|---|---|
| `@id` | URI | This ontology | Stable identifier for the place, e.g. `place:brixton` |
| `@type` | URI | schema.org | Always `Place`; boroughs also carry `AdministrativeArea` |
| `name` | string | OSM / common usage | Primary English name |
| `alternateName` | string[] | OSM / Wikidata | Known aliases and alternative spellings |
| `placeLevel` | URI | SKOS | One of `level:region`, `level:borough`, `level:neighbourhood`, `level:landmark` |
| `sameAs` | URI[] | Wikidata / Wikipedia / OSM | Equivalent URIs in external knowledge bases |
| `containsPlace` | URI[] | This ontology | Child places one level down |
| `containedInPlace` | URI | This ontology | Parent place one level up |
| `geo` | GeoCoordinates | OSM | Representative latitude/longitude |

### Borough-level additional properties

| Property | Type | Source | Description |
|---|---|---|---|
| `onsCode` | string | ONS | ONS statistical geography code, e.g. `E09000022` |
| `osmId` | string | OSM | OpenStreetMap relation ID |
| `governingBody` | object | OS / council websites | Name, URL and Wikidata ID of the borough council |
| `postalDistricts` | string[] | Royal Mail (indicative) | Postal districts that fall within or overlap the borough |
| `tflZones` | string[] | TfL Open Data | TfL fare zones |
| `boundarySource` | URI | ONS / legislation.gov.uk | Authoritative source for the boundary definition |
| `ward` | object | ONS | Electoral ward name and ONS code (neighbourhood level) |

## URI scheme

Place identifiers follow the pattern:

```
place:{slug}
```

Where `{slug}` is a lowercase, hyphenated identifier derived from the place name, e.g. `place:brixton`, `place:brixton-market`.

These are currently compact URIs (CURIEs). When the ontology is hosted at a stable domain, they will resolve to:

```
https://southlondonpost.place/place/{slug}
```

## Versioning

The ontology follows [Semantic Versioning](https://semver.org/):

- **MAJOR** version — breaking changes to the URI scheme or core schema structure
- **MINOR** version — new place nodes, new properties, extended coverage
- **PATCH** version — corrections to existing data (wrong coordinates, outdated names, etc.)

The current version is recorded in the `_meta.schemaVersion` field of the JSON-LD file.

## Extending the ontology

To add a new place node, it must include at minimum:

- `@id` — a unique slug URI
- `name` — primary name
- `placeLevel` — one of the four defined levels
- `containedInPlace` — parent node URI
- `sameAs` — at minimum one Wikidata URI or one OSM relation URI

See [`CONTRIBUTING.md`](../CONTRIBUTING.md) for the full submission process.
