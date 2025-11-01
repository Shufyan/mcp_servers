
# weather_typescript

Small TypeScript MCP server + CLI that builds to `build/index.js` and exposes a `weather` command.

## Quick start

1. Install dependencies

```bash
cd weather_typescript
npm install
```

2. Build

```bash
npm run build
```

3. Run

```bash
# run the built binary
npm run start

# development (watch TypeScript)
npm run dev
```

## .env

Create a `.env` file from `.env.example` when you need to provide secrets or overrides (e.g. `MODEL_CONTEXT_API_KEY`, `NWS_API_BASE`, `USER_AGENT`).

```bash
cp .env.example .env
# edit .env to fill real values
```

## Local CLI

To use the CLI locally:

```bash
# make the package available globally on your machine
npm link

# then run
weather
```

Or run the built file directly: `./build/index.js`.

## Project layout

- `src/` — TypeScript source
- `build/` — compiled output (distributed)
- `.env.example` — example env vars

## Notes

- `npm run build` sets executable permissions on `build/index.js`.
- The server uses stdio transport (not an HTTP port) by default.

- `npm run start` will run the build step before starting the binary (so you don't need to run `build` separately).
- `dotenv` is used for local `.env` loading and is included in devDependencies; run `npm install` to get it for development.

If you want, I can add a `start` script that builds before running, or add a lightweight test harness to exercise the CLI.
