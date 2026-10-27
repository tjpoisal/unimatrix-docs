# Unimatrix architecture and the 2.0 upgrade

Updated 2026-10-25. This guide describes the current code architecture, not a declaration that every hosted deployment exposes every feature.

## One memory layer, explicit access

Connected MCP clients and REST agents save and recall memory through the web application's customer-facing endpoints. The internal processing and worker services use PostgreSQL with pgvector as the durable store. Managed hosting and licensed Docker self-hosting share this service model.

Nested Spaces organize memories. Loom guides sources, import preview and approval. After the handoff, Librarian performs ongoing organization, extraction, contradiction handling, indexing and recall support. Its name refers to orchestration, not a particular language model.

## What 2.0 adds in code

The TypeScript server integration adds an Associative Memory Graph:

1. Indexed memories gain similarity and temporal connections.
2. Explicit activation recall starts with semantic matches and follows weighted relationships to connected context.
3. Use can reinforce co-activated graph connections without retraining a foundation model.
4. Contradiction interference and consolidation connect evolving and higher-level context to its sources.

Hybrid semantic/keyword recall remains available. Evidence-aware ranking, Veritas source lineage and temporal history help keep corrections traceable. Ranking signals are not probabilities of truth and conflicts can remain open for review.

## How to request it

Where advertised by the deployed endpoint, call `unimatrix_recall` with `query` and `activate: true`, or use `unimatrix_activate_memory` with a required natural-language `query`. The dedicated tool does not accept explicit seed IDs in the current implementation. Use the endpoint's advertised schema for supported fields.

Authentication uses your own API key at the customer web `/api/mcp` endpoint or the REST tools endpoint. Never publish a credential in a config example or repository. If the internal processing service is unavailable, local fallback search does not establish that associative activation ran.

## Availability and research

The upgrade requires matching web, processing and worker revisions, database migrations and valid internal configuration. A merge, math test or marketing page does not establish successful operation for a real client. Check the deployed tool list and actual save/index/recall/correction behavior.

The separate Rust reference implementation, numerical conformance vectors and hardware/CXL research are not a claim that the managed service runs on those components or achieves universal accuracy/latency improvements.

## Security

Memory content is encrypted at rest with AES-256-GCM. Inference, indexing and retrieval can process plaintext, and searchable derived data needs access controls. HTTPS/TLS protects configured public transport. This is not a universal zero-knowledge or end-to-end encrypted processing claim.

See [security](https://www.deployunimatrix.com/security), [MCP tools](https://www.deployunimatrix.com/docs/mcp), and [deployment](https://www.deployunimatrix.com/deployment). The website's redesigned architecture page and code upgrade notes are delivered in the companion website change; their deployment must be verified separately.
