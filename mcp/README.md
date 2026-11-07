# Groundtruth MCP server

This MCP server exposes the draft Groundtruth tools from Donovan's playbook. The repository currently has no `docs/CONTRACT.md` or official fixtures, so the inputs, envelope examples, and API route are provisional. Replace them with Monish's published contract before Phase 2.

## Run offline in mock mode

```bash
cd mcp
uv sync
GROUNDTRUTH_MOCK=1 uv run python -m mcp_server.server
```

The server uses stdio by default. It logs to stderr so stdout remains available for MCP messages. To use MCP Inspector:

```bash
cd mcp
GROUNDTRUTH_MOCK=1 uv run mcp dev mcp_server/server.py
```

## Claude Desktop

Use absolute paths for the repository and `uv` executable:

```json
{
  "mcpServers": {
    "groundtruth": {
      "command": "/absolute/path/to/uv",
      "args": ["--directory", "/absolute/path/to/Geospatial-SearchEngine/mcp", "run", "python", "-m", "mcp_server.server"],
      "env": {"GROUNDTRUTH_MOCK": "1"}
    }
  }
}
```

## Configuration

- `GROUNDTRUTH_MOCK=1` forces local mock fixtures.
- `GROUNDTRUTH_API_URL` is the provisional API base URL. Until the contract lands, the adapter posts to `/{tool_name}`; this route is an assumption, not an agreed contract.
- `GROUNDTRUTH_TIMEOUT_S` sets the HTTP timeout (default `60`). 5xx responses are retried three times with exponential backoff. On API errors, the server emits a warning to stderr and returns a fixture marked with an API-unavailable limit.
- `GROUNDTRUTH_LOG_LEVEL` sets log verbosity (default `INFO`).

Mock responses are illustrative and are never live search results. People-data requests are declined before mock or API dispatch. GeoJSON with more than 200 features is reduced to the first 50 features with a truncation note; envelope count and metrics are retained.

## Tests

```bash
cd mcp
uv sync --group dev
uv run pytest ../tests/mcp
```
