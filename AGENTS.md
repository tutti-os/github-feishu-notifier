# AGENTS.md

## Scope

This repository owns the Tutti organization GitHub to Feishu notification Worker.

It is intentionally small:

- `src/index.ts`: GitHub webhook verification, event filtering, contributor filtering, Feishu card formatting
- `wrangler.jsonc`: Cloudflare Worker configuration and bindings
- `worker-configuration.d.ts`: generated Worker binding types

Do not add unrelated organization governance files here. Organization-wide defaults belong in `tutti-os/.github`; new-repository scaffolding belongs in `tutti-os/repository-template`.

## Rules

- Never commit secrets, webhook URLs, GitHub tokens, or Feishu signing keys.
- Keep the GitHub Organization Webhook target at `/github`.
- Keep first-stage notifications lightweight: `issues`, `pull_request`, and `issue_comment` only.
- Filter bots, organization members, and repository collaborators before notifying Feishu.
- Preserve GitHub signature verification before parsing or trusting payloads.
- The Feishu bot currently requires the custom keyword `Github`, so card visible text must keep that exact spelling unless the bot security settings are updated.

## Checks

- `npm run check`
- `npm run deploy`

After changing card content, send a signed synthetic webhook and verify Feishu accepts it.
