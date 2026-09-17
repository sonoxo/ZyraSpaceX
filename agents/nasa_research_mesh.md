# NASA Research Mesh

## Goal

Create a scalable evidence-ingestion system for NASA public information without pretending to run an impossible number of literal agents.

## Architecture

1. **Seed Registry** — curated NASA domains, NTRS collections, handbooks and mission pages.
2. **Scheduler** — emits bounded research jobs.
3. **Fetch Workers** — retrieve permitted public pages while honoring site rules and rate limits.
4. **Parser Workers** — extract title, date, authors, document identifiers, sections and links.
5. **Classifier Workers** — tag content by ontology domain.
6. **Evidence Workers** — generate provenance, checksums and citations.
7. **Deduplication** — canonical URL + content hash.
8. **Human Review Queue** — required for engineering claims promoted into a design baseline.
9. **Knowledge Graph Loader** — maps approved evidence into ZyraSpace ontology.

## Scaling Model

Scale via queues and stateless workers, not by claiming 100,000,000 simultaneous agents. Practical production scaling uses concurrency limits, backoff, caching and incremental re-crawls.

## Research Domains

- systems engineering
- structures and materials
- thermal
- avionics
- GN&C
- communications
- power
- robotics
- propulsion (public high-level research only)
- ground systems
- launch operations
- recovery
- sustainable aviation
- electrified aircraft
- ISRU
- closed-loop life support
- space agriculture
- autonomy and digital engineering

## Guardrails

- public sources only
- respect robots.txt / terms / rate limits
- no credentialed scraping without authorization
- evidence provenance on every claim
- no automatic promotion of research text into flight-critical requirements
