<p align="center"><img src="assets/logo.png" alt="Business Event Space" width="128" height="128"></p>

# Business Event Space connector for Grok Bot

Remote MCP connector for [Business Event Space](https://businesseventspace.com): read venues, venue packs, event tools and suppliers with your own account and permissions. This plugin contains only manifests and this README; all logic runs on the hosted server.

## Network endpoints

| Endpoint | Purpose |
|---|---|
| `https://businesseventspace.com/mcp` | MCP, Streamable HTTP, protocol 2025-11-25 |
| `https://businesseventspace.com/.well-known/oauth-protected-resource` | RFC 9728 metadata |
| `https://businesseventspace.com/.well-known/oauth-authorization-server` | RFC 8414 metadata |
| `https://businesseventspace.com/oauth/authorize`, `/oauth/token`, `/oauth/register`, `/oauth/revoke` | OAuth 2.1 |

No other hosts are contacted.

## Credentials

Nothing to configure. On first use you sign in with your Business Event Space account and approve access (OAuth 2.1 with PKCE S256; dynamic client registration or client ID metadata documents). Access tokens last 15 minutes and refresh tokens rotate. Revoke any time under Account → Connect your Grok Bot.

## Tools (connector 2026.10.14.1)

Member grant (any account; the user can switch each action off):

| Tool | Title | Type |
|---|---|---|
| `me.get` | Who am I | read |
| `venues.list` | List venues | read |
| `venues.get` | Read a venue | read |
| `venue_pack.get` | Read a venue pack | read |
| `tools.search` | Search event tools | read |
| `suppliers.search` | Search suppliers | read |
| `enquiries.list_mine` | List my enquiries | read |
| `app_spec_index` | App spec index | read |
| `app_spec_get` | Read app spec | read |
| `whats_new` | What's new | read |
| `submit_feature_feedback` | Send feature feedback | write |

Ops grant (Business Event Space service account only, separate OAuth client, admin-approved): the member read tools plus

| Tool | Title | Type |
|---|---|---|
| `venues.create` | Create a venue | write |
| `venues.update` | Update a venue | write |
| `venues.levels_upsert` | Add or rename levels | write |
| `venues.rooms_upsert` | Add or update rooms | write |
| `dossier.section_update` | Update a venue pack section | write |
| `files.request_upload_url` | Get a file upload URL | write |
| `files.attach` | Attach an uploaded file | write |
| `undo` | Undo a change | write |

Generated from the live server's tool registry (`tools.json`); a server test fails if tools change without a changelog entry.

## Test prompts

1. "What can you do in Business Event Space?" (me.get, whats_new)
2. "List the venues you can see." (venues.list)
3. "Show me the levels and rooms at <a venue from the list>." (venues.get)
4. "Find event tools for countdown timers." (tools.search)
5. "Search suppliers in London for AV hire." (suppliers.search)
6. "Have I sent any enquiries?" (enquiries.list_mine)
7. "The connector can't export a venue pack as PDF. Can you tell the team?" (the bot must ask before calling submit_feature_feedback)

A reviewer account (member grant, no MFA) is available to marketplace reviewers on request from enquire@businesseventspace.com.

## Links

- Docs: https://businesseventspace.com/docs/grok-bot-connector
- Privacy: https://businesseventspace.com/privacy
- Terms: https://businesseventspace.com/terms
- Support: https://businesseventspace.com/support

License: MIT
