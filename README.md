# Claude Code with persistent memory (agent_utils)

Give Claude Code memory that survives across sessions and machines, using the hosted
**agent_utils Memory** MCP service. No local server to run.

## Setup (one approval)

```bash
TOKEN=sk_$(openssl rand -hex 32)
claude mcp add --scope user --transport http agent-utils-memory \
  https://memory.agent-utils.ai/mcp --header "Authorization: Bearer $TOKEN"
```

The first call auto-provisions a free trial (1,000 credits, no card). Activate later at
`https://accounts.agent-utils.ai/setup?token=$TOKEN` ($5, 500,000-credit limit).

## Make every session memory-aware

Append to `~/.claude/CLAUDE.md`:

```md
## Persistent Memory
You have persistent memory via the agent-utils-memory MCP tools.
At the start of each conversation, call list_namespaces to check for stored context.
```

## What this demonstrates

Context restoration across sessions with a single hosted MCP server. The same token also
unlocks locks, idempotency, and unit conversion - see the
[agent-utils hub](https://codeberg.org/agent-utils/agent-utils).

## License

MIT. agent_utils is a hosted commercial service; this example is not the service.
