# Installing the ASOMap MCP server (for AI agents)

ASOMap is a hosted remote MCP server. There is nothing to install or build: add the URL to the
client's MCP settings.

- URL: `https://asomap.com/mcp`
- Transport: streamable HTTP
- Auth: OAuth 2.1 with dynamic client registration, or an API key sent as
  `Authorization: Bearer <key>`

## Steps

1. Ask the user for their ASOMap API key. If they have none, they sign up at https://asomap.com
   (free plan, no card) and create one on the **API keys** page (https://asomap.com/keys).
   The key is shown once.
2. Add the server to the MCP settings (for Cline, `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "asomap": {
      "type": "streamableHttp",
      "url": "https://asomap.com/mcp",
      "headers": {
        "Authorization": "Bearer <ASOMAP_API_KEY>"
      },
      "disabled": false
    }
  }
}
```

   A client that supports MCP OAuth can leave out `headers`: on the first call the server answers
   401 with a `WWW-Authenticate` header pointing to the sign-in, and the user clicks Allow.
3. Check the connection by calling `status`, then `myApps` to list the user's tracked apps.

## Good first requests

- "Review my app": ranks that dropped, keywords close to the top 10, missing keywords.
- "Find new keywords for Germany" (`suggestKeywords`, `discover`).
- "Compare me with <competitor>" (`compare`, `competitorGaps`).

Every tool is documented at https://asomap.com/mcp-docs. Support: support@asomap.com
