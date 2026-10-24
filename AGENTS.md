<!-- BEGIN:nextjs-agent-rules -->

## This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->

# Hackathon project rules

- Read `HACKATHON_HANDOFF.md` and the exact event prompt before making product decisions.
- Read `TEAM_COORDINATION.md` and recent `coordination/updates/` files when starting substantial work. Leave a concise update at meaningful milestones so agents using other tools or laptops can catch up.
- For a direct Slack request or handoff, send the short acknowledgement from `TEAM_COORDINATION.md` as its own Slack message before any substantive reply. Do not combine the status and your answer in one message; send the answer or update separately when ready.
- Ask the team to agree on a small demo before adding features. Do not invent requirements or select extra services without a reason.
- Explain unfamiliar commands in plain language when guiding the beginner on the team.
- Keep changes focused and preserve existing working behavior. Coordinate before changing shared files another teammate is editing.
- Never put credentials in source files, chat prompts, screenshots, or commits. Use `.env.local`, which Git ignores.
- Do not commit or push unless the user asks. Before claiming work is done, summarize what changed and what remains to try manually.
- Follow the Next.js instructions in the generated block above and consult the installed Next.js guide under `node_modules/next/dist/docs/` before changing app code.
