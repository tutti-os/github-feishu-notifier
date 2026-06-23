# GitHub Feishu Notifier

Cloudflare Worker for forwarding selected external contribution events from the `tutti-os` GitHub organization to a Feishu group card.

## Flow

```text
GitHub Organization Webhook
-> Cloudflare Worker /github
-> signature verification
-> event, bot, member, collaborator, and duplicate filtering
-> Feishu custom bot card
```

## Events

The first-stage notification scope is intentionally lightweight:

- `issues`
- `pull_request`
- `issue_comment`

Supported actions:

- `opened`
- `reopened`
- `ready_for_review`
- `created`

The Worker does not notify for review events, workflow events, pushes, releases, or internal organization member activity.

## Cloudflare

Worker name:

```text
tutti-github-feishu-notifier
```

Required secrets:

```text
GITHUB_WEBHOOK_SECRET
GITHUB_TOKEN
FEISHU_BOT_WEBHOOK
```

Optional secret:

```text
FEISHU_BOT_SIGN_KEY
```

## Commands

```sh
npm install
npm run check
npm run deploy
```

Health check:

```text
https://tutti-github-feishu-notifier.1551403343.workers.dev/health
```
