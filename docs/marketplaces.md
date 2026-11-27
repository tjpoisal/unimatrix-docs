# Unimatrix companion distribution

Prepared 2026-11-27. This public package contains connection metadata and three user-facing workflow skills. Product source remains private. CC BY 4.0 applies to the companion instructions and metadata in this repository. It does not license the hosted service, private implementation, names or marks.

## Install in Claude Code

```text
/plugin marketplace add tjpoisal/unimatrix-docs
/plugin install unimatrix@unimatrix-plugins
```

The plugin requests a scoped Unimatrix API key through its sensitive configuration field. Create a key in your account under Settings → API Keys. The plugin connects to `https://www.deployunimatrix.com/api/mcp`. Never paste a real key into a tracked configuration file or a marketplace submission. With Claude Code versions supporting plugin user configuration, use `/plugin configure unimatrix@unimatrix-plugins` to change it. Older clients can configure the HTTP server manually using the client-specific documentation.

For local review run `claude plugin validate /absolute/path/to/unimatrix-docs`, then load with `claude --plugin-dir /absolute/path/to/unimatrix-docs`. Discover tools through the connected client. Test a disposable project handoff, recall it, inspect its sources and remove only that test record through the supported deletion workflow.

## Install in Cursor

Cursor uses `.cursor-plugin/plugin.json`, the root `mcp.json`, and the same `skills/` directory. Configure `UNIMATRIX_API_KEY` in Plugins → Configure. The variable schema declares the key without including a real credential. Submit the public repository at https://cursor.com/marketplace/publish after a real client test.

## Portable companion skills

```bash
npx skills add tjpoisal/unimatrix-docs --skill unimatrix-resume
npx skills add tjpoisal/unimatrix-docs --skill unimatrix-handoff
npx skills add tjpoisal/unimatrix-docs --skill unimatrix-source-review
```

These instructions also require an authenticated Unimatrix tool connection. Installing a skill alone does not connect an account or enable automatic conversation capture. Other agents must support the required tools or be configured with an implemented REST adapter.

## Listing copy

Unimatrix gives supported AI clients access to explicitly stored project memory through MCP. Resume a project with sourced context, save a concise checkpoint for another client, or review a source before approving memory ingestion. The free companion requires a Unimatrix account and scoped key. Tool availability depends on the connected service and client. Processing may require plaintext within the service's trusted boundary. Memory and source lineage support review, with unresolved conflicts and uncertainty preserved.

## Pricing and paid workflows

The companion package is free. The source pricing reviewed on 2026-11-27 lists Pro at $9/month or $79/year, Business at $39/user/month or $390/user/year with five users minimum, and Enterprise starting at $1,500/month. Consult https://www.deployunimatrix.com/pricing for current offers. This package does not change billing or grant entitlements. Live checkout and plan provisioning still require verification.

Keep ordinary connection, recall and handoff instructions free. A separate paid pilot may offer a reviewed knowledge-import report or a scoped migration/onboarding engagement. State document limits, supported sources, expected deliverable, review steps and support duration. Price only after measuring processing and support costs. Proposed metering or additional allowances must be implemented and tested before being advertised.

## Channel status

Repository marketplace, Cursor connection package and portable skills are prepared here. Official Claude/Cursor approvals, Agensi listing, and live authenticated client verification are pending. The public `server.json` describes the hosted remote for directory submission. Registry publication requires namespace verification and its own successful receipt. Glama's open-source hosting path does not imply that Unimatrix's proprietary service can be mirrored publicly. Smithery is a discovery directory following its proxy shutdown.

Use https://www.agensi.io/sell for a free companion listing first and confirm support for an externally hosted authenticated MCP. Test a paid workflow separately after pricing and deliverables are validated. ChatGPT app commerce eligibility needs separate confirmation for digital subscriptions. GitHub Marketplace and Apify require additional product integrations and are later channels.

Campaign links may target https://www.deployunimatrix.com/quickstart with `utm_source`, `utm_medium=marketplace`, and `utm_campaign=unimatrix-companion`. Attribution implementation remains pending. Measure account connection, first explicit save and successful scoped recall, seven-day repeat use, conversion and support time through disclosed collection.

## References

https://code.claude.com/docs/en/plugins/manifest-reference

https://cursor.com/docs/reference/plugins

https://skills.sh/docs/faq

https://www.agensi.io/terms

https://registry.modelcontextprotocol.io/
