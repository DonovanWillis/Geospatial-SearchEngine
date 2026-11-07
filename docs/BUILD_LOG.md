# Build log

## Donovan:

- 2026-11-07 14:46 ET — Added the mock-mode MCP server, nine draft tools, local versioned response fixtures, the `groundtruth://about` resource, API retry/fallback adapter, MCP client smoke check, and 15 offline tests. Verified that the stdio client lists and calls all nine tools, receives a structured envelope plus concise text summary, and that all 15 tests pass.
- 2026-11-07 14:57 ET — `origin/main`, the engine contract, fixtures, and API URL are still unavailable. Built the Phase 3 mock map agent with rules planning, an optional OpenAI-compatible planner, people-data declines, bounded validated tool calls, configured Mecklenburg demo places, CLI output, and JSON Schema map actions. The four required mock CLI requests run; export reports unavailability rather than offering a fake file. Live dispatch waits for the contract.
