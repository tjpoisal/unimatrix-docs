# Connecting an AI client to Unimatrix over MCP

The customer-facing Model Context Protocol endpoint is provided by the Unimatrix web app at:

```
https://www.deployunimatrix.com/api/mcp
```

You authenticate with your Unimatrix API key (a `umx_...` token issued in your account's
**Settings → API Keys** page on deployunimatrix.com).

## Configuration

For Claude Code, add the following project `.mcp.json` entry and provide
`UNIMATRIX_API_KEY` through the client environment. Other clients have different
transport and credential fields; use the client-specific examples below.

```json
{
  "mcpServers": {
    "unimatrix": {
      "type": "http",
      "url": "https://www.deployunimatrix.com/api/mcp",
      "headers": { "Authorization": "Bearer ${UNIMATRIX_API_KEY}" }
    }
  }
}
```

The service authenticates the `Authorization: Bearer ...` header. Keep real keys
out of tracked files. The companion plugin can prompt for the key directly.
See [marketplace installation](marketplaces.md).

## Tool surface

The endpoint exposes a memory toolset over MCP. At the time of writing the production tools
include:

- `unimatrix_list_spaces`, `unimatrix_get_space`, `unimatrix_create_space`,
  `unimatrix_create_child_space` — workspaces and their hierarchy
- `unimatrix_store_memory` — save a memory from the current conversation
- `unimatrix_search_memories` — semantic search across all memories
- `unimatrix_list_memories`, `unimatrix_update_memory`
- `unimatrix_get_recent` — most recent memories across all devices/LLMs; a good first call in a new
  session to continue where a previous model left off

The live, authoritative list is always the docs page:

```
https://www.deployunimatrix.com/docs/mcp
```

## Developer tools

Developer-facing AI tools accept a remote MCP server. The endpoint and bearer-token contract are shared, while support and field names
vary by client. Historical examples below were documented on 2026-09-05 and require
validation against the installed client version.

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

- Memory written from any connected AI/device is available to every other connected AI/device.
- Content is encrypted at rest and access is explicit per-tool, with audit logging.
- Self-hosted instances expose the same MCP surface at their own `/api/mcp` route (or `/mcp` on the
  app's MCP service); configure your URL to match your deployment.