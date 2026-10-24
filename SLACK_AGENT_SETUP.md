# Slack setup for coding agents

Use Slack for quick coordination during the hackathon. Use `coordination/updates/` in this repo for durable updates that every agent can read after pulling the latest changes.

The project channel is [#sasehacks2026 in the flhasbhang workspace](https://app.slack.com/client/T0CBTFS6X5G/C0CCN2V2AQY). It is a public channel within that Slack workspace. Open the link after joining the workspace; the channel currently has one member, so the team still needs to join it. If you are not a workspace member, ask the team lead to add you to the workspace first.

## One-time setup

1. Join the team's Slack workspace and ask a workspace admin to approve Slack MCP access if the connection is blocked.
2. Join the team's project channel (the human team lead should share its name or invite you).
3. Connect Slack separately inside each agent harness you use. Each teammate should sign in as themselves; do not share OAuth tokens or passwords.
4. In the agent, ask it to read the project channel before work and post a short status there when starting or handing off.

Slack MCP uses this endpoint: `https://mcp.slack.com/mcp`.

## Claude Code

In Claude Code, install Slack's official plugin:

```text
/plugin install slack@claude-plugins-official
```

Follow the browser sign-in prompt. Or add the server from a terminal:

```bash
claude mcp add --transport http --scope local slack https://mcp.slack.com/mcp
```

Then run `/mcp` in Claude Code and finish Slack sign-in. `--scope local` keeps the connection on that computer instead of adding machine-specific authentication settings to the shared repo.

## Gemini CLI

Gemini CLI can connect to remote MCP servers. Edit its local `settings.json` and add a Slack entry under `mcpServers` (merge it into existing settings; do not replace other settings):

```json
{
  "mcpServers": {
    "slack": {
      "httpUrl": "https://mcp.slack.com/mcp",
      "oauth": {
        "clientId": "YOUR_SLACK_APP_CLIENT_ID"
      }
    }
  }
}
```

Use the Slack app client ID supplied by the workspace administrator, then restart Gemini CLI and follow its OAuth prompts. Slack MCP may require a registered Slack app and administrator approval; Gemini's support for remote MCP alone does not guarantee that the Slack OAuth flow will work. Do not paste a client secret or token into this repository.

## Antigravity

In Antigravity, open the agent panel's **… → MCP Servers → Manage MCP Servers → View raw config**. Add this entry to the existing `mcpServers` object:

```json
{
  "slack": {
    "serverUrl": "https://mcp.slack.com/mcp",
    "oauth": {
      "clientId": "YOUR_SLACK_APP_CLIENT_ID"
    }
  }
}
```

Alternatively, add it to your personal `~/.gemini/config/mcp_config.json`. Use the Slack app client ID supplied by the workspace administrator. Save, then use Antigravity's **Authenticate** control and complete the browser sign-in. Antigravity support for remote MCP does not guarantee that Slack OAuth is enabled for the workspace; an admin may need to approve or configure the app.

## If Slack cannot connect

- Ask the workspace admin to approve the Slack MCP integration and provide the correct app client ID.
- Ensure the Slack app is an internal app or published in the Slack Marketplace; Slack documents that unlisted apps cannot use MCP.
- If your harness does not support Slack MCP, continue through GitHub: pull the latest branch, read `AGENTS.md`, `HACKATHON_HANDOFF.md`, and the newest `coordination/updates/` note, then add your own update file before handing off.
- Slack MCP is a tool the agent can use when asked; it is not a background listener that guarantees instant alerts.

## Safety and collaboration

- Each person signs in with their own account. Never share an OAuth token, password, or API key.
- An agent can read or send Slack messages only within the permissions granted to its own connection. Check messages and channel membership before relying on it.
- Before editing shared files, state your plan in Slack and check that another teammate is not changing the same files.
- Write important decisions, blockers, and handoffs to `coordination/updates/` and commit/push only when the human lead has authorized it.

## Official references

- [Slack: Connect its MCP server to agent harnesses](https://docs.slack.dev/ai/slack-mcp-server/connect-to-harnesses/)
- [Gemini CLI: MCP servers](https://google-gemini.github.io/gemini-cli/docs/tools/mcp-server.html)
- [Antigravity: MCP configuration and OAuth](https://www.antigravity.google/docs/mcp)
