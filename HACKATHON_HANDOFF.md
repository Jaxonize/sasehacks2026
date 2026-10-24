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
6. On another teammate's computer, accept the GitHub invite first, then run:

   ```bash
   git clone https://github.com/Jaxonize/sasehacks2026.git
   cd sasehacks2026
   npm install
   ```

7. The Vercel project `sasehacks2026` already exists in the `Flashbang Robotics` team. To turn on automatic deploys, connect GitHub to Vercel first (instructions below), then open the project and connect `Jaxonize/sasehacks2026` under **Settings → Git**. Vercel will create preview deployments when teammates push changes. Share a preview URL with the team and judges.

## Git basics

- **Clone** means make a working copy on another teammate's computer.
- **Commit** means save a named checkpoint in Git.
- **Push** means upload your commits to GitHub.
- **Pull** means download your teammates' latest commits.
- Keep commits small. Before editing the same file as someone else, tell the team.

The repository is private. `@equinochrome` has been invited; GitHub shows the invite as pending until they accept it. Ask the other teammate for their GitHub username and invite them from **Settings → Collaborators**.

## Stack and accounts

- **Next.js + TypeScript + Tailwind:** website framework, programming language, and styling tools already installed here.
- **GitHub:** shared code repository is ready. This folder is connected to `origin/main`, and the starter files have been pushed.
- **Supabase:** the connected account has one organization and three inactive existing projects. None was selected for this hackathon. Create a new project only if the agreed idea needs a database, accounts, file storage, or live updates. Copy its Project URL and publishable key into `.env.local`; keep secret/service-role keys on the server only.
- **Vercel:** a Next.js project named `sasehacks2026` exists in the `Flashbang Robotics` team, and this computer's ignored `.vercel/project.json` points this folder at it. No deployment exists yet. Vercel requires a GitHub login connection on the account before it can import the repo. In Vercel, open your profile menu → **Settings → Authentication → Add New → GitHub**, sign in and authorize the GitHub account that owns `Jaxonize/sasehacks2026`. Then open the Vercel project → **Settings → Git** and connect that repository. Vercel will then deploy pushes automatically. The Vercel CLI is installed globally, but it still needs `vercel login` before local deployments. The `.vercel` folder is intentionally ignored by Git; on another computer, run `vercel link --project sasehacks2026 --scope flashbang-robotics` after signing in.
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
