# SSR Service

SSR Service runs a Vite server entry in Node.js to render application components as HTML. Call it
through the `ssr` command or send a JSON request to its HTTP renderer. PHP applications can call it
through [SSR Bridge](https://github.com/codemonster-ru/ssr-bridge).

## Get started

Use Node.js 22, the version tested in CI. Install the service in a project with a Vite SSR build.
The [Vue playground](playgrounds/vue) shows how to build the client assets and the server entry.

```bash
npm install @codemonster-ru/ssr-service
npx ssr server --serverEntry ./dist/server/entry-server.js
```

The server defaults to port `3001`. The `POST /render` request body contains `component` and `props`.
Use a component identifier recognized by your server entry. The `ssr render` command reads the same
JSON from standard input and writes HTML to standard output.

## Configuration

Set these values with CLI flags or environment variables. Relative paths resolve from the current
working directory. Run `npx ssr server --help` for all options.

| Environment variable | CLI flag | Default |
| --- | --- | --- |
| `MODE` | `--mode` | `production` |
| `PORT` | `--port` | `3001` |
| `CLIENT_PATH` | `--clientPath` | `dist/client` |
| `SERVER_ENTRY` | `--serverEntry` | `dist/server/entry-server.js` |
| `MANIFEST_PATH` | `--manifestPath` | `dist/client/manifest.json` |
| `CLIENT_ENTRY` | `--clientEntry` | `/assets/entry-client.js` |
| `DEV_ROOT` | `--devRoot` | Empty |
| `DEV_ENTRY_SERVER` | `--devEntryServer` | `./src/entry-server.ts` |

The renderer can add scripts, styles, and preload links using the client build manifest.

## Development and support

From the repository root, run the same test setup as [CI](.github/workflows/tests.yml).

```bash
npm ci
npm install --prefix playgrounds/vue
npm run test:ci
```

Use [GitHub Issues](https://github.com/codemonster-ru/ssr-service/issues) for questions and reproducible bugs.
Follow the [contribution guide](./CONTRIBUTING.md) to propose changes.
Report vulnerabilities through the [security policy](./SECURITY.md).

Licensed under the [MIT License](LICENSE).
