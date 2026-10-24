# Team and agent coordination

Use Discord for quick, live team conversation. Use this repository for the durable record so agents on other laptops and in other coding tools can catch up without controlling anyone's desktop.

## When an agent starts

1. Pull the latest repository changes.
2. Read `AGENTS.md`, `HACKATHON_HANDOFF.md`, and the latest files in `coordination/updates/`.
3. Before substantial work, say in Discord what you plan to do if you can access Discord. If you cannot, tell the human who started you so they can avoid assigning the same work twice.
4. Coordinate before changing files another teammate or agent is already editing.

## How to leave a durable update

Create or update one file per agent session in `coordination/updates/`, named with the date, time, and agent, for example `2026-10-24-0900-codex.md`. Include:

- Who and which agent/harness
- What you worked on and its status
- Files or pull request changed
- Decisions, questions, or blockers
- The next action or who owns the handoff

Keep updates short. Never put passwords, API keys, private environment values, or other secrets in Discord, Git, or these notes. Commit and push updates when the human has authorized that; otherwise leave them local and tell the human they need to push for teammates to see them. Important decisions from Discord should be copied here.

## Live agent access

An agent can read Discord only if its own harness has a Discord integration configured and authorized for the team's server/channel. Desktop control on one computer does not give agents on other laptops access to that app. If an agent has no Discord integration, use the repo update process above and have the human relay urgent messages through Discord.

The GitHub repository is private, so each teammate needs to accept the repository invitation and sign in to GitHub on their own computer. Never share one person's tokens with another teammate or agent.
