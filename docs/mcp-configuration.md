# Connecting an AI client to Unimatrix over MCP

The customer-facing Model Context Protocol endpoint is provided by the Unimatrix web app at:

```
https://www.deployunimatrix.com/api/mcp
```

You authenticate with your Unimatrix API key (a `umx_...` token issued in your account's
**Settings → MCP** page on deployunimatrix.com).

## Configuration

Use the configuration format supported by your client. The required transport is HTTP MCP and the request must carry `Authorization: Bearer <your API key>`. A generic `apiKey` property is not a universal client schema. Use the [client quickstart](https://www.deployunimatrix.com/quickstart) and the client-specific examples below; verify the installed client's supported format/version.

## Tool surface

Inspect the deployed endpoint's advertised tools and [MCP reference](https://www.deployunimatrix.com/docs/mcp). Space discovery, explicit store/search, recent memory, hybrid recall, sessions and Loom workflow tools have different requirements.

The 2.0 code adds optional associative activation through `unimatrix_recall` with `activate: true`, or `unimatrix_activate_memory` with a required `query`. This is not enabled on every search. Matching deployed services and migrations are required; see [architecture and availability](architecture.md).

## Developer tools

Developer-facing AI tools accept a remote MCP server. The same endpoint and bearer token work
everywhere; the field names differ per client. Examples originate from the September 2026 client review; installed-client compatibility has not been reverified for every client in this documentation update.

### opencode

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "unimatrix": {
      "type": "remote",
      "url": "https://www.deployunimatrix.com/api/mcp",
      "headers": { "Authorization": "Bearer {env:UNIMATRIX_MCP_TOKEN}" },
      "oauth": false
    }
  }
}
```

`type` must be `"remote"`, and `oauth: false` is required so opencode sends the token instead of
attempting MCP OAuth. Verify with `opencode mcp list` / `opencode mcp debug unimatrix`.

### Claude Code

```bash
claude mcp add --transport http --scope user unimatrix https://www.deployunimatrix.com/api/mcp \
  --header "Authorization: Bearer $UNIMATRIX_MCP_TOKEN"
```

In a project `.mcp.json` the entry must include `"type": "http"` (a URL-only entry fails silently).
Environment expansion `${UNIMATRIX_MCP_TOKEN}` keeps secrets out of git.

### Cline

In `cline_mcp_settings.json` (VS Code globalStorage), the transport type is `"streamableHttp"` —
omitting it defaults to the deprecated SSE transport and fails:

```json
{
  "mcpServers": {
    "unimatrix": {
      "type": "streamableHttp",
      "url": "https://www.deployunimatrix.com/api/mcp",
      "headers": { "Authorization": "Bearer umx_your_api_key" }
    }
  }
}
```

### Zed

In `settings.json` under `context_servers`; include the `Authorization` header to skip the OAuth
prompt (Unimatrix uses API keys, not OAuth):

```json
{
  "context_servers": {
    "unimatrix": {
      "url": "https://www.deployunimatrix.com/api/mcp",
      "headers": { "Authorization": "Bearer umx_your_api_key" }
    }
  }
}
```

### VS Code / GitHub Copilot

Workspace `.vscode/mcp.json` (or user-config via **MCP: Open User Configuration**), then confirm
the server-trust prompt:

```json
{
  "servers": {
    "unimatrix": {
      "type": "http",
      "url": "https://www.deployunimatrix.com/api/mcp",
      "headers": { "Authorization": "Bearer umx_your_api_key" }
    }
  }
}
```

## Notes

- Memory can be recalled by another properly authenticated client within the same authorized scope; it is not automatically injected into every conversation.
- Content is encrypted at rest and access is explicit per-tool, with audit logging.
- Self-hosted clients should use the web origin’s `/api/mcp` route. The internal processing service address is not the recommended customer endpoint.