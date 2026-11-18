# KV Freight

KV Freight is a landing-page web application for a freight network offering air, ocean, road, and customs brokerage services under one team.

<img width="1900" height="889" alt="Screenshot 2026-11-18 211548" src="https://github.com/user-attachments/assets/7ae3cd69-2ef1-4f4c-8a25-91158ad8ce22" />

## Tech stack

- [Vite](https://vite.dev/) (dev server and build tooling)
- [React 19](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
- [Tailwind CSS](https://tailwindcss.com/) (v4, via `@tailwindcss/vite`)
- [Motion](https://motion.dev/) for animations
- [Lucide React](https://lucide.dev/) for icons
- [Google GenAI SDK](https://ai.google.dev/) (`@google/genai`) for Gemini-powered features

## Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended)
- npm (included with Node.js)

## Getting started

1. **Install dependencies**

   ```bash
   npm install
   ```

2. **Configure environment variables**

   Copy the example file and fill in the required values:

   ```bash
   copy .env.example .env
   ```

   On macOS/Linux:

   ```bash
   cp .env.example .env
   ```

   | Variable | Description |
   | --- | --- |
   | `GEMINI_API_KEY` | API key for Gemini requests (configure via your environment/secrets provider). |
   | `APP_URL` | Public URL where the app is hosted (used for self-referential links/callbacks as needed). |

3. **Start the development server**

   ```bash
   npm run dev
   ```

   The app runs at [http://localhost:3000](http://localhost:3000) (configured with `--host=0.0.0.0 --port=3000`).

## Available scripts

| Script | Command | Description |
| --- | --- | --- |
| `dev` | `npm run dev` | Start the Vite development server on port 3000. |
| `build` | `npm run build` | Create a production build in `dist/`. |
| `preview` | `npm run preview` | Preview the production build locally. |
| `lint` | `npm run lint` | Run TypeScript type-checking (`tsc --noEmit`). |
| `clean` | `npm run clean` | Remove `dist/` and `server.js` (Unix-style command). |

> **Note:** The `clean` script uses `rm -rf`, which may not work in Windows Command Prompt. Use PowerShell (`Remove-Item -Recurse -Force dist,server.js`) or Git Bash if needed.

## VS Code debugging

A sample launch configuration is provided in [`.vscode/launch.json`](.vscode/launch.json).

1. Start the dev server: `npm run dev`
2. In VS Code, open **Run and Debug** and select **Launch Chrome (Vite dev server)** or **Launch Edge (Vite dev server)**.
3. Set breakpoints in your source files and reload as needed.

The debugger attaches to `http://localhost:3000` with `webRoot` set to the workspace folder.

## Project structure

```text
.
├── .vscode/            # Editor/debug configuration
├── public/             # Static public assets
├── src/                # Application source (React/TypeScript)
│   ├── App.tsx
│   ├── main.tsx
│   └── index.css
├── index.html          # HTML entry point
├── vite.config.ts      # Vite configuration
├── tsconfig.json       # TypeScript configuration
├── package.json
└── .env.example        # Example environment variables
```

## Notes

- Vite is configured with path alias `@` pointing to the project root (`vite.config.ts`).
- During builds, a custom Vite plugin copies `src/assets` into `dist/src/assets` so root-relative asset URLs continue to resolve in production.
- If `DISABLE_HMR=true` is set in the environment, Vite HMR and file watching behavior are adjusted as defined in `vite.config.ts`.
