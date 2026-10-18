# Claude Code with persistent memory (agent_utils)

Give Claude Code memory that survives across sessions and machines, using the hosted
**agent_utils Swarm** MCP server. No local server to run.

## Setup (one approval)

```bash
TOKEN=sk_$(openssl rand -hex 32)
claude mcp add --scope user --transport http agent-utils-swarm \
  https://mcp.agent-utils.ai/swarm --header "Authorization: Bearer $TOKEN"
```

The first call auto-provisions a free trial (1,000 credits, no card). Activate later at
`https://mcp.agent-utils.ai/setup?token=$TOKEN` ($5, 500,000-credit limit).

## Make every session memory-aware

Append to `~/.claude/CLAUDE.md`:

```md
## Persistent Memory
You have persistent memory via the agent-utils-swarm MCP tools.
At the start of each conversation, call list_namespaces to check for stored context.
```

## What this demonstrates

Context restoration across sessions with a single hosted MCP server. The same server also
gives you locks, a task board, pub/sub, idempotency and webhook inboxes, and the same token
works on the extensions server (math, units, currency) - see the
[agent-utils hub](https://github.com/agent-utils/agent-utils).

## License

MIT. agent_utils is a hosted commercial service; this example is not the service.
