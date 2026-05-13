# Active personal branches

`main` is a strict fast-forward mirror of `upstream/main`.
`deploy` is rebuilt from `main` plus the branches below.

| Branch | Type | Purpose | Upstream PR |
|---|---|---|---|
| `feat/model-fallback-chain` | feat | Model fallback chain support | n/a |
| `fix/telegram-routing-dream` | fix | Telegram session/topic routing and Dream status/test fixes | n/a |
| `feat/telegram-polling-healthcheck` | feat | Telegram polling healthcheck scripts and container wiring | n/a |
| `local/ci-deploy` | local | Fork-specific deploy Docker workflow | n/a |
| `local/meta` | local | Fork workflow docs and branch registry | n/a |

## Recipe

`deploy` is rebuilt from `main` with:

```bash
git checkout deploy
git reset --hard main
for b in \
  feat/model-fallback-chain \
  fix/telegram-routing-dream \
  feat/telegram-polling-healthcheck \
  local/ci-deploy \
  local/meta
do
  git merge --no-ff "$b" -m "deploy: include $b"
done
```

