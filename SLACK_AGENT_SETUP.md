# Slack setup for coding agents

Use Slack for quick coordination during the hackathon. Use `coordination/updates/` in this repo for durable updates that every agent can read after pulling the latest changes.

The project channel is [#sasehacks2026 in the flhasbhang workspace](https://app.slack.com/client/T0CBTFS6X5G/C0CCN2V2AQY). It is public to members of that Slack workspace. Join the workspace first, then open the channel link. If you are not a workspace member, ask the team lead to invite you.

## One-time setup

1. Join the team's Slack workspace and ask a workspace admin to approve Slack MCP access if the connection is blocked.
2. Join the team's project channel (the human team lead should share its name or invite you).
3. Connect Slack separately inside each agent harness you use. Each teammate should sign in as themselves; do not share OAuth tokens or passwords.
4. In the agent, ask it to read the project channel before work and post a short status there when starting or handing off.

Slack MCP uses this endpoint: `https://mcp.slack.com/mcp`.

## ChatGPT Slack app connection (used by this task)

The current Codex/ChatGPT Slack connection is an app connector; it works without controlling the Slack browser tab and is separate from an MCP server configuration.

1. In ChatGPT, open **Settings → Apps** or **Settings → Plugins** (the label depends on the account interface), then choose Slack or the plugin that includes it.
2. If ChatGPT offers **Install plugin**, install it. Then choose **Connect**, sign into the `flhasbhang` workspace with your own Slack account, and approve the requested connection.
3. In a task, make sure Slack tools are available. Ask the agent to find `#sasehacks2026`, read the recent messages, and post a short test/status message.

This setup was verified from this task by listing the `flhasbhang` workspace, finding and reading the channel, and posting a message with Slack's connector. [The verification message is here](https://flhasbhang.slack.com/archives/C0CCN2V2AQY/p1792811875024609). The channel ID is `C0CCN2V2AQY`; agents should search by channel name instead of relying on IDs. If Slack tools are missing, check that the app/plugin is installed and the account is connected, then refresh or start a task where Slack is available. ChatGPT app availability can vary by plan, workspace, account, and interface. This app connection applies to that user's ChatGPT environment; it does not sign other harnesses in.

To check that the connection works, have the agent list Slack workspaces, search for `#sasehacks2026`, read its recent messages, and send a routine verification or status message. A Slack tab being open is not itself a connection; these steps should use the harness's Slack tools/API.

## Codex CLI

Codex CLI uses the same Slack remote MCP server as other harnesses. From a terminal, run:

```bash
codex mcp add --transport http slack https://mcp.slack.com/mcp
```

Complete the browser OAuth prompt, then verify with:

```bash
codex mcp list
```

Look for `slack` with status `connected`. You can also configure it in `~/.codex/config.toml`:

```toml
[mcp_servers.slack]
url = "https://mcp.slack.com/mcp"
auth = "oauth"
```

After editing that file, run `codex mcp login slack`. The Codex CLI connection is local to that computer and account.

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

## Getting a laptop and agent caught up

On a new laptop, do these steps in order:

1. Accept the private GitHub repository invitation and sign into GitHub with your own account.
2. Clone the repo and install its locked dependencies:

   ```bash
   git clone https://github.com/Jaxonize/sasehacks2026.git
   cd sasehacks2026
   npm ci
   ```

3. Join the `flhasbhang` Slack workspace, open [#sasehacks2026](https://app.slack.com/client/T0CBTFS6X5G/C0CCN2V2AQY), and connect Slack to your harness using the instructions above.
4. Start the agent from the repository folder. Have it read `AGENTS.md`, `TEAM_COORDINATION.md`, `HACKATHON_HANDOFF.md`, the exact event prompt, and the newest files in `coordination/updates/` before making product changes.
5. Ask it to read recent Slack messages and post its task ownership before editing. Coordinate with the team if someone else is changing the same files.
6. For handoff, add a short timestamped note in `coordination/updates/` covering harness, status, changed files, decisions/blockers, and next owner. Push only when the human team lead has authorized it.

If the project folder is already cloned, first run `git status --short --branch`. If it is clean, use `git pull --ff-only origin main` to catch up. If it has uncommitted work, pause and coordinate before pulling or switching branches so nobody loses work.

Install the Node.js version recorded in `.nvmrc` (currently 24) if it is missing on your laptop. `npm ci` installs the exact package versions recorded by this repo. Start the app with `npm run dev` when you need a local preview. Only create `.env.local` if the agreed demo requires a connected service; never commit it.

## Official references

- [Slack: Connect its MCP server to agent harnesses](https://docs.slack.dev/ai/slack-mcp-server/connect-to-harnesses/)
- [OpenAI: Connect Slack in ChatGPT](https://help.openai.com/en/articles/12525822-using-slack-in-chatgpt)
- [OpenAI: Connected apps in ChatGPT](https://help.openai.com/en/articles/11487775-connected-apps-in-chatgpt)
- [Gemini CLI: MCP servers](https://google-gemini.github.io/gemini-cli/docs/tools/mcp-server.html)
- [Antigravity: MCP configuration and OAuth](https://www.antigravity.google/docs/mcp)
