# Team and agent coordination

Use the team's Slack channel for quick, live team conversation. Use this repository for the durable record so agents on other laptops and in other coding tools can catch up without controlling anyone's desktop. See [`SLACK_AGENT_SETUP.md`](./SLACK_AGENT_SETUP.md) for connecting Claude Code, Gemini CLI, and Antigravity.

## When an agent starts

1. Pull the latest repository changes.
2. Read `AGENTS.md`, `HACKATHON_HANDOFF.md`, and the latest files in `coordination/updates/`.
3. Before substantial work, say in the team's Slack channel what you plan to do if your harness has Slack connected. If you cannot, tell the human who started you so they can avoid assigning the same work twice.
4. Coordinate before changing files another teammate or agent is already editing.

## How to leave a durable update

Create or update one file per agent session in `coordination/updates/`, named with the date, time, and agent, for example `2026-10-24-0900-codex.md`. Include:

- Who and which agent/harness
- What you worked on and its status
- Files or pull request changed
- Decisions, questions, or blockers
- The next action or who owns the handoff

Keep updates short. Never put passwords, API keys, private environment values, or other secrets in Slack, Git, or these notes. Commit and push updates when the human has authorized that; otherwise leave them local and tell the human they need to push for teammates to see them. Important decisions from Slack should be copied here.

## Live agent access

An agent can read Slack only if its own harness has Slack MCP configured and authorized for the team's workspace. Desktop control on one computer does not give agents on other laptops access to Slack. If an agent cannot connect, use the repo update process above and ask a teammate to relay urgent messages in Slack. Slack MCP lets an agent use Slack when prompted; it does not automatically monitor every new message.

The GitHub repository is private, so each teammate needs to accept the repository invitation and sign in to GitHub on their own computer. Never share one person's tokens with another teammate or agent.
