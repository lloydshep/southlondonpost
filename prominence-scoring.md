# Prominence scoring

This document describes the rules used to rank content items in the South London Post aggregator. The goal is to surface the most significant and trustworthy local content at the top of each place's feed.

## Overview

Each content item receives a **prominence score** between 0 and 100. Items are ranked in descending order of prominence within each place page. The score is a weighted combination of four signals:

| Signal | Weight | Description |
|---|---|---|
| Source credibility tier | 50% | The tier of the publishing source (see below) |
| Recency | 30% | How recently the item was published |
| Place specificity | 15% | How specifically the item relates to the selected place |
| Engagement (future) | 5% | Reserved for future signals (shares, comments, etc.) |

## Source credibility tiers

Sources are assigned to one of four tiers. Tier assignment is editorial and reviewed periodically.

| Tier | Description | Examples |
|---|---|---|
| 1 | Established local and national press; official council sources | South London Press, Southwark News, Lambeth Council, The Guardian (local) |
| 2 | Local independent media; established event and listings APIs | Brixton Buzz, Peckham Peculiar, Time Out London, Eventbrite |
| 3 | Community sites, hyperlocal blogs, moderated forums | Urban 75, r/southlondon (Reddit) |
| 4 | Social media and unmoderated platforms | X / Twitter, Nextdoor |

### Tier score mapping

| Tier | Base score contribution (out of 50) |
|---|---|
| 1 | 50 |
| 2 | 35 |
| 3 | 20 |
| 4 | 10 |

## Recency scoring

Recency is scored on a decay curve. An item published within the last hour receives the full 30 points; items older than 7 days receive 0.

| Age | Recency score (out of 30) |
|---|---|
| < 1 hour | 30 |
| 1–6 hours | 25 |
| 6–24 hours | 18 |
| 1–3 days | 10 |
| 3–7 days | 4 |
| > 7 days | 0 |

## Place specificity scoring

An item that names the selected place explicitly in its title or body scores higher than one that merely covers a parent geography.

| Match type | Specificity score (out of 15) |
|---|---|
| Exact match to selected place | 15 |
| Match to child place of selected place | 12 |
| Match to sibling place in same borough | 6 |
| Match to parent place only | 3 |

## Example calculation

> Item: "Brixton Market traders threatened by rent hike"
> Source: South London Press (Tier 1)
> Age: 2 hours
> Selected place: Brixton Market (exact match)

| Signal | Score |
|---|---|
| Source credibility (Tier 1) | 50 |
| Recency (2 hours) | 25 |
| Place specificity (exact match) | 15 |
| **Total** | **90** |

## Future signals

The 5% engagement weight is reserved for signals not yet implemented:

- Number of social shares or comments (where retrievable via API)
- Manual editorial boost (for significant stories that may not score highly on recency alone)
- Suppression flag (to remove inappropriate or outdated content)

## Principles

- **Transparency:** Scoring rules are documented publicly and versioned alongside the ontology.
- **Source-agnostic within tiers:** All Tier 1 sources are treated equally; the algorithm does not favour one Tier 1 outlet over another.
- **No paid placement:** Source tier is assigned editorially, not commercially. No source can pay to improve its tier.
- **Reviewable:** Tier assignments are recorded in the source registry and can be contested via a GitHub issue.
