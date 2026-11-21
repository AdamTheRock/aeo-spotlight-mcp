# AEO Spotlight MCP server

A remote, hosted MCP server for [AEO Spotlight](https://aeospotlight.com/). It lets Claude and other MCP clients read your AI visibility data: whether ChatGPT, Gemini, Google AI Overviews, Perplexity, DeepSeek, Grok, Claude and Microsoft Copilot mention your brand, which pages they cite, and who they name instead. Clients can also take a few guarded actions on that data.

This repository holds documentation only. The server is hosted, so there is nothing to install or self-host.

- **Endpoint:** `https://api.aeospotlight.com/mcp` (Streamable HTTP)
- **Auth:** OAuth 2.1 (dynamic client registration and PKCE) for Claude, or an `X-API-Key` header for other clients
- **Docs:** https://aeospotlight.com/developers
- **Requires:** an AEO Spotlight account ([free plan available](https://aeospotlight.com/pricing))

## Connect

**Claude (claude.ai or desktop):** open Settings → Connectors → Add custom connector, and enter:

```
https://api.aeospotlight.com/mcp
```

Sign in to AEO Spotlight, pick the brand, and choose the access level: read only, or read and draft.

**Claude Code, or any MCP client with an API key:**

```sh
claude mcp add --transport http aeo-spotlight https://api.aeospotlight.com/mcp --header "X-API-Key: <your key>"
```

Create the key under Developer API keys in AEO Spotlight.

## Tools

There are 26 tools.

**17 read** your monitoring data:
- tracked questions
- AI answers
- cited sources
- competitors
- visibility gaps
- content opportunities
- drafts
- jobs
- credits

**9 take actions:**
- run a tracked question
- detect gaps
- generate a brief or draft
- fact-check and revise a draft
- approve or dismiss a suggestion
- propose publishing

There is no publish tool. Proposing creates an approval request that a person approves inside AEO Spotlight.

Actions that run AI engines or write drafts use your account credits, and they count against the connection's daily credit limit. To disconnect, revoke the "Claude connector" key under Developer API keys.

## Example prompts

- "Which of my tracked questions don't mention my brand, and who do the AI answers name instead?"
- "Which pages does Perplexity cite most for my category?"
- "Draft a page for my biggest visibility gap, then fact-check it."

## Support

support@aeospotlight.com
