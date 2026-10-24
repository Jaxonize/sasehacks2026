# SASE Hacks 2026 Starter

A beginner-friendly web app workspace prepared for the SASE Hacks 2026 prompt. The app is a plain Next.js starter; it does not assume what your team will build.

## Start the app

You need Node.js 20.9 or newer. Node.js 24 is already installed on the setup computer.

```bash
npm install
npm run dev
```

Open <http://localhost:3000>. Keep the terminal open while you work. Stop the app with `Ctrl+C`.

## First steps tomorrow

1. Read [`HACKATHON_HANDOFF.md`](./HACKATHON_HANDOFF.md) with your team.
2. Paste the exact hackathon prompt into your AI coding tool and ask it to help you agree on the smallest demo that satisfies the judging criteria.
3. Put the agreed goal and team roles in the handoff doc.
4. Build one working path through the demo before adding extra features.
5. Run the app locally. GitHub pushes automatically deploy through the connected Vercel project; the current starter preview is <https://sasehacks2026-nu.vercel.app>. Read the handoff guide about SSO before sharing a link with judges.

## Useful commands

```bash
npm run dev       # run locally while you build
npm run lint      # check code style
npm run build     # prepare a production build
```

## Stack

- Next.js App Router, React, and TypeScript
- Tailwind CSS for styling
- Node.js 24 is recorded in `.nvmrc` so compatible Node version managers can select the same version; `.editorconfig` keeps indentation and line endings consistent across editors
- Git and GitHub for shared version history
- Supabase is available if the idea needs a database, login, file storage, or realtime updates
- Vercel automatically deploys GitHub pushes; see the handoff guide for the current URL and access note

Choose Supabase and Twilio only if the prompt needs them. A static or local-only demo can skip extra services.

## Secrets

Copy `.env.example` to `.env.local` only after you create/connect the services you need. Never commit `.env.local`, passwords, service-role keys, or provider tokens. Only browser-safe publishable keys belong in variables beginning with `NEXT_PUBLIC_`.

## AI coding agents

The shared project rules are in [`AGENTS.md`](./AGENTS.md). Claude Code reads [`CLAUDE.md`](./CLAUDE.md); Gemini and Antigravity read [`GEMINI.md`](./GEMINI.md), and Antigravity also discovers `AGENTS.md`. Start any agent in this repository folder so it sees the right files.
