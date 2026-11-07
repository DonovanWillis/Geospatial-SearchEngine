# Requests for Monish

## 2026-11-07 14:44 ET — Publish MCP contract and fixtures

**What:** Please publish `docs/CONTRACT.md` and `docs/fixtures/` with the canonical tool names, input schemas, endpoint paths, versioned envelopes, API base URL, and examples for each implemented tool.

**Why:** Donovan's MCP server currently follows the playbook's draft tool list and uses provisional schemas and a provisional `/{tool_name}` POST route. It needs the engine contract before live MCP work can be safely wired in Phase 2.

**Workaround meanwhile:** Use local fixtures in `GROUNDTRUTH_MOCK=1` mode. No live API request is made during the smoke test.
