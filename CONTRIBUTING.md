# Contributing to South London Post

Thank you for your interest in contributing. This project welcomes contributions in three areas: **place data**, **source registry**, and **documentation**.

## Before you start

Please read the following before submitting anything:

- [`docs/borough-inclusion-rule.md`](docs/borough-inclusion-rule.md) — which boroughs are in scope and why
- [`docs/ontology-guide.md`](docs/ontology-guide.md) — the ontology structure and required properties
- [`docs/sources.md`](docs/sources.md) — how sources are attributed and which licences apply

## Types of contribution

### 1. Adding a place node

Use the **Place addition** issue template to propose a new neighbourhood or landmark. Include:

- The proposed place name and any known aliases
- The parent place it belongs to (which borough and neighbourhood)
- A Wikidata URI or OpenStreetMap relation/way ID as evidence
- The ONS ward it falls within, if known

New place nodes are reviewed for:
- Scope (must be within one of the five boroughs)
- Naming (primary name should match OSM and/or Wikidata)
- Hierarchy (must have a clearly defined parent)
- Source quality (at minimum one `sameAs` link required)

### 2. Correcting existing data

Use the **Data correction** issue template to report:

- Incorrect coordinates
- Wrong or missing `sameAs` links
- Outdated names or aliases
- Missing ward or ONS code

Please include a link to the authoritative source that supports the correction.

### 3. Adding or correcting a source

To propose a new content source for the aggregator, or to contest a tier assignment, open a plain issue with:

- The source name and URL
- The proposed tier (1–4) with justification
- The RSS feed URL, API endpoint, or scraping approach
- Any licence restrictions on the content

Tier assignments are editorial decisions made by project maintainers. No source can pay for a tier upgrade.

### 4. Documentation improvements

Pull requests that improve clarity, fix typos, or add missing information to the docs are always welcome. No issue needed for small fixes.

## Pull request process

1. Fork the repository
2. Create a branch named `place/your-place-name` or `fix/description`
3. Make your changes
4. Validate the JSON-LD is well-formed: `python3 -m json.tool ontology/south-london-ontology.jsonld`
5. Open a pull request with a clear description of what changed and why

## Code of conduct

This project follows the [Contributor Covenant Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/). Be respectful, assume good faith, and keep discussions focused on the data.

## Licence of contributions

By contributing to this repository, you agree that your contributions will be published under the same [CC BY 4.0 licence](https://creativecommons.org/licenses/by/4.0/) as the rest of the project. Contributions that incorporate OSM data are additionally subject to the [ODbL share-alike obligation](https://opendatacommons.org/licenses/odbl/).
