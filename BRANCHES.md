# Active personal branches

`main` is a strict fast-forward mirror of `upstream/main`.
`deploy` is rebuilt from `main` plus the branches below.

| Branch | Type | Purpose | Upstream PR |
|---|---|---|---|
| `feat/telegram-polling-healthcheck` | feat | Telegram polling healthcheck scripts and container wiring | n/a |
| `feat/telegram-allowed-chat-members` | feat | Telegram per-chat access rules via `chatAccess` | n/a |
| `local/ci-deploy` | local | Fork-specific deploy Docker workflow | n/a |
| `local/meta` | local | Fork workflow docs and branch registry | n/a |

## Superseded branches

| Branch | Status |
|---|---|
| `feat/model-fallback-chain` | Superseded by upstream model fallback support in `main`. |
| `fix/telegram-routing-dream` | Superseded by upstream Telegram topic/session and Dream command updates in `main`. |

## Recipe

`deploy` is rebuilt from `main` with:

```bash
git checkout deploy
git reset --hard main
for b in \
  feat/telegram-polling-healthcheck \
  feat/telegram-allowed-chat-members \
  local/ci-deploy \
  local/meta
do
  git merge --no-ff "$b" -m "deploy: include $b"
done
```
