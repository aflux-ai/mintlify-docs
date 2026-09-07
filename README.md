# Aflux documentation

Public documentation for [Aflux](https://aflux.ai) — an AI media buyer for Telegram channels.

Live at **[docs.aflux.ai](https://docs.aflux.ai)**. Built on [Mintlify](https://mintlify.com); pushing to `main` deploys.

## Layout

| Tab | Source |
|---|---|
| Documentation | Hand-written guides — `introduction`, `quickstart`, `concepts`, `guides/`, `billing/`, `account/` |
| API reference | `api/` overview pages, plus endpoint pages **generated from the live OpenAPI document** at `https://backend.aflux.ai/openapi` |
| MCP | `mcp/` — the Model Context Protocol server and its 37 tools |

Because the endpoint pages are generated from the deployed spec, they cannot drift from the API. To change one, change `src/main/resources/openapi/api.yaml` in the backend.

## Develop

```bash
npm i -g mint   # needs an LTS Node release
mint dev        # http://localhost:3000
mint broken-links
```

## Conventions

See [`AGENTS.md`](AGENTS.md) — terminology, where each fact comes from, and what must not be documented.
