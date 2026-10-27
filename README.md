# Unimatrix — public documentation

Unimatrix is a shared persistent memory layer for supported AI tools. Save decisions and context through a connected client, then explicitly recall relevant memory elsewhere. Sources, relationships and corrections help preserve the reason behind an answer.

- **Connections:** MCP-capable clients, REST integrations, supported browser extensions, and desktop/mobile surfaces have different setup paths. Browser capture support does not imply a native MCP connection in every chat site.
- **Memory:** hybrid retrieval, source lineage, temporal history and evidence-aware ranking are part of the memory architecture.
- **2.0 code upgrade:** the TypeScript server implementation adds an Associative Memory Graph, explicit activation recall, reinforcement, interference handling and consolidation links. See the architecture guide for the boundary between source implementation and hosted availability.
- **Control:** content encryption at rest, scoped access, tenant isolation and licensed Docker self-hosting. Processing can require plaintext; this is not a universal end-to-end encrypted memory service.

The product source is proprietary and private. This repository contains only approved public documentation, not product source, internal runbooks or customer data.

## Start here

| Resource | Guide |
| --- | --- |
| Product | [Unimatrix](https://www.deployunimatrix.com) |
| Architecture | [2.0 overview](docs/architecture.md) |
| Client setup | [MCP configuration](docs/mcp-configuration.md) |
| Quickstart | [Connect a client](https://www.deployunimatrix.com/quickstart) |
| MCP tools | [Tool reference](https://www.deployunimatrix.com/docs/mcp) |
| REST | [API reference](https://www.deployunimatrix.com/docs/api) |
| Documentation | [Docs hub](https://www.deployunimatrix.com/docs) |
| Security | [Security model](https://www.deployunimatrix.com/security) |
| Hosting | [Deployment](https://www.deployunimatrix.com/deployment) |
| Release notes | [Code upgrade notes](https://www.deployunimatrix.com/changelog) |
| Press | [Media kit](docs/media-kit.md) |

## Contributing

Update architecture, client setup and public claims together. Distinguish code implementation, testing and deployed availability. Never mirror private source or credentials into this repository.

## License and contact

Documents are licensed under [CC BY 4.0](LICENSE). Unimatrix names, logos and marks remain property of Cimbro LLC. Contact: **hello@deployunimatrix.com**.
