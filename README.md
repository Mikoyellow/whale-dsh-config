# whale-dsh-config

Stable public bootstrap/update manifests for the YG whale Android apps.

Current cpolar base: `https://10d42afb.r38.cpolar.top`

Updated: `2026-10-28T23:45:00+08:00`

App bootstrap URL:

```
https://raw.githubusercontent.com/Mikoyellow/whale-dsh-config/main/bootstrap.json
```

## Per-app manifest directories (collect v1.19 / manage v1.9 / tavern v1.9)

These three apps now read their manifest from their own directory in this repo — the app
appends `/update.json` to its default address — and fall back to the current cpolar tunnel
when GitHub is unreachable:

| app | directory | manifest | version |
| --- | --- | --- | --- |
| 鲸鲸收集 (yg-info) | `collect/` | `main/collect/update.json` | v1.19 (code 20) |
| 鲸鲸管理 (whale-manage) | `manage/` | `main/manage/update.json` | v1.9 (code 10) |
| 鲸鲸酒馆 (whale-tavern) | `tavern/` | `main/tavern/update.json` | v1.9 (code 10) |

Each per-app `update.json` is the same content as that app's `dist/update.json`. Its `apk`
field is an absolute cpolar URL, because the repo only hosts manifests, not APK bytes:

- collect → `https://10d42afb.r38.cpolar.top/info/update.apk`
- manage → `https://10d42afb.r38.cpolar.top/whale-manage/update.apk`
- tavern → `https://10d42afb.r38.cpolar.top/whale-tavern/update.apk`

When cpolar changes, update `bootstrap.json`, the `apk`/`manifest`/`base` fields in each
per-app `update.json`; the apps pick the change up without a new build.

## Legacy root manifests

Root-level `*.json` (dsh, whale-surf, whale-create, whale-clean, omnihub, jinjing-collect,
whale-manage, whale-tavern) are kept as before for the older apps that still read them.
