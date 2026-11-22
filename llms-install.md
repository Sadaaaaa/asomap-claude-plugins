# Installing the ASOMap MCP server (for AI agents)

ASOMap is a hosted remote MCP server. There is nothing to install or build: add the URL to the
client's MCP settings.

- URL: `https://asomap.com/mcp`
- Transport: streamable HTTP
- Auth: OAuth 2.1 with dynamic client registration, or an API key sent as
  `Authorization: Bearer <key>`

## Steps

1. Ask the user for their ASOMap API key first, before writing any settings. If they have none,
   they sign up at https://asomap.com (free plan, no card) and create one on the **API keys** page
   (https://asomap.com/keys). The key is shown once. Never write a placeholder such as
   `<ASOMAP_API_KEY>` into the settings: a server with a placeholder key fails to connect.
2. Add the server to the client's **existing** MCP settings file. Don't create a new file in the
   project or workspace: the client won't read it. For Cline it's the file its MCP Servers panel opens
   ("Configure MCP Servers"):
   - Cline in VS Code (macOS): `~/Library/Application Support/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json`
   - Cline in VS Code (Windows): `%APPDATA%\Code\User\globalStorage\saoudrizwan.claude-dev\settings\cline_mcp_settings.json`
   - Cline in VS Code (Linux): `~/.config/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json`
   - Cline CLI: `~/.cline/data/settings/cline_mcp_settings.json`

   Merge this entry into its `mcpServers` object, keeping the servers already there:

```json
{
  "mcpServers": {
    "asomap": {
      "type": "streamableHttp",
      "url": "https://asomap.com/mcp",
      "headers": {
        "Authorization": "Bearer <the key the user gave>"
      },
      "disabled": false
    }
  }
}
```

   A client that supports MCP OAuth can leave out `headers` (and skip step 1): on the first call the
   server answers 401 with a `WWW-Authenticate` header pointing to the sign-in, and the user clicks
   Allow in the browser.
3. Cline reloads the settings file by itself; other clients may need a restart. Check the connection
   by calling `status`, then `myApps` to list the user's tracked apps. A new account has no apps yet:
   add one with `addMyApp` and its App Store, Google Play or RuStore link.

## Good first requests

- "Review my app": ranks that dropped, keywords close to the top 10, missing keywords.
- "Find new keywords for Germany" (`suggestKeywords`, `discover`).
- "Compare me with <competitor>" (`compare`, `competitorGaps`).

Every tool is documented at https://asomap.com/mcp-docs. Support: support@asomap.com
