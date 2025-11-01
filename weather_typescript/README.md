
# weather_typescript

Minimal TypeScript package that builds to `build/index.js` and exposes a CLI entrypoint `weather`.

## Prerequisites

- Node.js (v18+ recommended)
- npm (or pnpm/yarn) available on PATH
- A POSIX-like shell if you need to run the `chmod` step (macOS / Linux)

## Install

Clone the repository and install dependencies from the `weather_typescript` folder:

```bash
# from repo root
cd weather_typescript
npm install
```

If you prefer pnpm or yarn, use those instead (this project uses the standard `package.json`).

## .env (optional)

This project does not hard-code environment variables, but if your runtime needs configuration, create a `.env` file in `weather_typescript/` with variables the program expects. Example placeholders:

```env
# Example environment variables you might need
PORT=3000
API_KEY=your_api_key_here
MODEL_CONTEXT_API_KEY=your_modelcontext_api_key
```

Notes:
- Do not commit `.env` to git; a `.gitignore` is provided to exclude it.
- Replace the example names above with the real names your code expects.

## Build

Compile TypeScript to the `build/` folder:

```bash
npm run build
```

This runs `tsc` and then sets executable permissions on `build/index.js` (the package's `bin`). The built file is placed in `build/index.js` and is what you'll run in production.

## Run

- Run directly with node:

```bash
node build/index.js
```

- Or install the package locally as a global CLI (useful if the package exposes a command via `bin`):

```bash
# from inside weather_typescript/
npm link

# then you can run the CLI as
weather
```

If `npm link` is not desired, you can also run the local binary directly:

```bash
./build/index.js
```

## Packaging / Publishing

The package.json marks `build` as a distributed file. If you publish this package, ensure you run the build step before publishing so the `build/` folder is included.

## Development Notes

- Source lives in `src/` and compiles into `build/`.
- Types are provided via `@types/node` and TypeScript is a dev dependency.
- The package depends on `@modelcontextprotocol/sdk` and `zod` per `package.json`.

## Troubleshooting

- If `npm run build` fails, ensure TypeScript (`typescript`) and `@types/node` are installed as devDependencies and your `tsconfig.json` is correct.
- If the CLI doesn't run after `npm link`, check that `build/index.js` is executable (`chmod +x build/index.js`) and has a proper shebang (e.g. `#!/usr/bin/env node`) if used as a CLI.

## Quick checklist

- [ ] npm install
- [ ] npm run build
- [ ] export any required env vars (or create `.env`)
- [ ] node build/index.js  (or `npm link` + `weather`)

---

If you'd like, I can also:
- Add convenience npm scripts for `start` and `dev`.
- Add an example `.env.example` file with the variables your code reads.
- Add a small test harness to exercise the built binary.
