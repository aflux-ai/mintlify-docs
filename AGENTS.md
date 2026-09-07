# Documentation project instructions

## About this project

- The public documentation for **Aflux** — an AI media buyer that finds Telegram channels, negotiates each placement with the channel owner and publishes, with the advertiser approving every deal.
- Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter; configuration lives in `docs.json`.
- English only, matching the landing at `aflux.ai`.

## Where the facts come from

The backend is the source of truth, not this repository.

- **API reference is generated**, not written. `docs.json` points the *Endpoints* group at the live OpenAPI document, `https://backend.aflux.ai/openapi`. Never hand-write an endpoint page — fix the spec in the backend instead and it appears here on the next build.
- **Guides are written from the spec's own prose.** Field descriptions in `api.yaml` are unusually detailed (ad-copy markup rules, `destinationUrl` placeholders, what each analytics metric measures). Quote and explain those; do not invent behaviour.
- **Before documenting a status code, check it.** The spec only declares a `default` error response. The concrete codes live in `coffee.swap.adflux.common.error`: 400, 401, 402, 403, 404, 409, 500, 502. There is no 422.
- **MCP tool names** come from the `@Component` classes in `coffee.swap.adflux.mcp.tool`. There are 37.

## Terminology

| Use | Not |
|---|---|
| Aflux | AdFlux |
| project, campaign, placement | account, order, booking |
| channel owner | publisher, admin, seller |
| ad copy | creative text, post text |
| balance | wallet, credits |

Domains: the site is `aflux.ai`, the console `console.aflux.ai`, the API `backend.aflux.ai`, the click redirect `go.aflux.ai`. Never `.io`.

## Style preferences

- Active voice, second person ("you").
- One idea per sentence. Sentence case for headings.
- Bold for UI elements: Click **Settings**. Code formatting for file names, commands, paths, fields and endpoints.
- Money is always a decimal **string** in examples — `"500.00"`, never `500.0`.
- Say what a call costs before saying how to make it. `create_campaign` and campaign creation spend the whole budget; that belongs above the fold, not in a footnote.

## Content boundaries

- Document the advertiser's surface only. The internal API (`/internal`), the back-office API (`/office`) and the operator tooling are not public and must not appear here.
- Do not document authentication internals beyond what an integrator needs: no token formats, no hashing details beyond "keys are stored hashed".
- No screenshots of real advertiser data.

## Design

`style.css` carries the landing's visual system — the tokens are `adflux-landing/app/globals.css` verbatim, so the two surfaces read as one product. Keep selectors generic: Mintlify's internal class names are not a public API and anything keyed on them breaks on their next release.

## Local preview

```bash
npm i -g mint
mint dev
```

Mintlify's CLI needs an **LTS** Node release; it refuses to run on odd-numbered ones.
