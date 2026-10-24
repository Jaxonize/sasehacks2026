# Hackathon handoff

## What is ready

- Private GitHub repository: [Jaxonize/sasehacks2026](https://github.com/Jaxonize/sasehacks2026)
- Local Next.js starter in this folder using TypeScript, Tailwind CSS, ESLint, and npm
- `AGENTS.md` for shared agent instructions, plus `CLAUDE.md` and `GEMINI.md` for Claude Code, Gemini, and Antigravity
- `.env.example` with safe placeholders; real service keys do not belong in Git
- Node.js and npm are installed on the setup computer

## Tomorrow morning: quick start

1. Get the official project prompt and judging criteria. Paste them into your AI assistant and ask it to help the team turn them into one simple demo and a short task list.
2. Agree on who owns the interface, data/backend, and presentation. Add the names and agreed goal below.
3. Open this folder in your editor or coding agent. Read `AGENTS.md`; Claude Code also reads `CLAUDE.md`, and Antigravity/Gemini read `GEMINI.md`.
4. Start the website from a terminal in this folder:

   ```bash
   npm install
   npm run dev
   ```

5. Open <http://localhost:3000>. Save changes with Git as the team works; push them to GitHub so everyone can get the latest copy.
6. When the demo works locally, import this GitHub repository into Vercel and add any environment variables the app needs. Share the resulting preview link with the team and judges.

## Git basics

- **Clone** means make a working copy on another teammate's computer.
- **Commit** means save a named checkpoint in Git.
- **Push** means upload your commits to GitHub.
- **Pull** means download your teammates' latest commits.
- Keep commits small. Before editing the same file as someone else, tell the team.

The repository is private and `@equinochrome` has been invited; GitHub shows the invite as pending until they accept it. Ask the other teammate for their GitHub username and invite them from **Settings → Collaborators**.

## Stack and accounts

- **Next.js + TypeScript + Tailwind:** website framework, programming language, and styling tools already installed here.
- **GitHub:** shared code repository is ready. This computer's Git remote and first push are still to be connected after a local commit.
- **Supabase:** the connected account has one organization and three inactive existing projects. None was selected for this hackathon. Create a new project only if the agreed idea needs a database, accounts, file storage, or live updates. Copy its Project URL and publishable key into `.env.local`; keep secret/service-role keys on the server only.
- **Vercel:** the connected Vercel account currently needs reauthentication. Reconnect it in Codex or sign in to Vercel from your coding tool before creating a deployment. Import the GitHub repository for automatic preview deploys.
- **Twilio:** no Twilio account connection is available in this workspace. Add it only if the prompt needs SMS, phone calls, or WhatsApp; keep credentials on the server and do not put them in `NEXT_PUBLIC_` variables.

Connected apps in Codex do not automatically sign Claude Code or Antigravity into GitHub, Supabase, Vercel, or Twilio. Each tool may need its own sign-in or MCP setup. Do not copy access tokens between tools. Use the account's normal sign-in flow and give agents only the access needed for the hackathon.

## Fill this in after the prompt arrives

- **Official prompt / judging criteria:**
- **One-sentence idea:**
- **Smallest demo that proves it:**
- **Team members and roles:**
- **Services the idea actually needs:**
- **Who is presenting:**

## If something gets stuck

- If `npm run dev` says a package is missing, run `npm install` from this folder.
- If port 3000 is already in use, stop the other app or follow the alternate address printed in the terminal.
- If a service key is missing, keep building the UI with sample data and connect the service later.
- If an AI tool loses context, ask it to read `HACKATHON_HANDOFF.md` and `AGENTS.md` before continuing.
