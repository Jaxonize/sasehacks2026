# Codex and Antigravity handoff

## Project setup

Antigravity is configured on the setup laptop to open the same repository folder Codex uses, not a second copy. On another laptop, add that laptop's cloned repository folder as an Antigravity project. Antigravity discovers `AGENTS.md` and `GEMINI.md` in the workspace. The rules in `AGENTS.md` apply to both tools. Start Antigravity from its `sasehacks2026` project in the Projects sidebar.

## Before handing work from one agent to another

1. Tell the team in `#sasehacks2026` what you are finishing and who is taking over, if your agent can access Slack.
2. Ask the current agent to stop editing, save its files, and summarize the goal, decisions, changed files, unfinished work, and any commands it ran.
3. In the repository terminal, run `git status --short --branch`. This shows whether files have changed and which branch is checked out.
4. Add a short dated note in `coordination/updates/` with the summary and next action. Commit and push only when the human team lead has authorized it.
5. Start the next agent from this same folder. Ask it to read `AGENTS.md`, `HACKATHON_HANDOFF.md`, `TEAM_COORDINATION.md`, this file, the exact event prompt, and the newest coordination update before editing.
6. Have the next agent inspect Git status and read the handoff note before it continues. If both agents are open, only one should edit the shared folder at a time.

Do not use `git reset`, discard changes, or switch branches to “clean up” a handoff unless the human team lead explicitly asks. If the previous agent left uncommitted work, review it with the team and continue from it or coordinate a safe save first.

## Catching up on another laptop

Clone the public repository and install the locked dependencies:

```bash
git clone https://github.com/Jaxonize/sasehacks2026.git
cd sasehacks2026
npm ci
```

`npm ci` installs the exact library versions recorded in the repo. Anyone can clone the public repository; teammates need GitHub collaborator write access to push to the original. Do not copy local `.env.local`, `.vercel`, or OAuth credentials between laptops. Set up each tool’s service connections on that laptop using [`SLACK_AGENT_SETUP.md`](./SLACK_AGENT_SETUP.md).

## Service access

The Slack connector available to Codex is separate from Antigravity’s MCP connection. Antigravity needs its own authorized Slack MCP connection to read or post channel messages. The setup laptop currently has the Antigravity project open, but Slack is not yet connected inside Antigravity. Follow the Antigravity section of [`SLACK_AGENT_SETUP.md`](./SLACK_AGENT_SETUP.md); Slack MCP may require a workspace-approved Slack app client ID. Never put that ID’s secret, OAuth tokens, or passwords in this repo. If Slack is unavailable, use the coordination update files and GitHub as the handoff log.

Vercel, Supabase, GitHub, and other ChatGPT/Codex connections also do not automatically sign in Antigravity or another teammate’s tools. Each user should connect their own account through the tool’s normal authentication flow. Keep service secrets in the ignored `.env.local` file, and only add integrations the team’s agreed demo needs.

## After the official prompt arrives

Fill in the prompt and agreed demo in [`HACKATHON_HANDOFF.md`](./HACKATHON_HANDOFF.md). The agents should help the team plan the smallest demo first; do not invent features or services before the team agrees.
