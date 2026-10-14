# Changelog

## 2026.10.14.1

Connector phase 1: OAuth hardening, member and ops grants, lean tool set, feedback.

- OAuth per MCP auth spec 2025-11-25: protected-resource metadata, DCR, PKCE S256, audience check, 15-minute access tokens, rotating refresh tokens.
- Member tools: me.get, venues.list, venues.get, venue_pack.get, tools.search, suppliers.search, enquiries.list_mine, whats_new, submit_feature_feedback, app_spec_index, app_spec_get.
- Ops tools (ops grant only): venues.create, venues.update, venues.levels_upsert, venues.rooms_upsert, dossier.section_update, files.request_upload_url, files.attach, undo.
- Older tools (directory_*, suppliers_*, searchers_*, account_*, grok_bot_*) are no longer listed on /mcp.
