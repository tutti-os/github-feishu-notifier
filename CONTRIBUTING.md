# Contributing

Thank you for improving the Tutti GitHub Feishu notifier.

## Development

Install dependencies:

```sh
npm install
```

Validate the Worker bundle:

```sh
npm run check
```

Deploy:

```sh
npm run deploy
```

## Pull Requests

- Use a Conventional Commit style PR title, such as `fix: trim notification card`.
- Keep changes focused on the notification service.
- Do not commit secrets or local `.dev.vars` files.
- Document any change to GitHub webhook events, Cloudflare bindings, or Feishu bot keyword requirements.

## Runtime Secrets

The Worker expects these Cloudflare secrets to exist:

- `GITHUB_WEBHOOK_SECRET`
- `GITHUB_TOKEN`
- `FEISHU_BOT_WEBHOOK`
- `FEISHU_BOT_SIGN_KEY` is optional.
