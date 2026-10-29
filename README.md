# Market

The app store of astraOS. It shows the catalog of the astra cloud server
(github.com/tsryzenstech/astra-cloud): the Today page (stories, App and Game of
the Day, top apps, new apps), apps by category, search and updates.

## Changing the server

Edit `config.json` and push. GitHub Actions (`.github/workflows/release.yml`)
builds `com.astra.market.apkg` with a new versionCode and publishes it as a
release. With the `ASTRA_CLOUD_TOKEN` secret (an admin session token of astra
cloud, see below) and optionally the `ASTRA_CLOUD_URL` variable, the release is
also uploaded to Market itself, so phones get it as an update.

To get a token: `curl -X POST <server>/api/auth/login -H 'Content-Type: application/json' -d '{"email":"…","password":"…","device":{"name":"CI"}}'`
and copy `token` (it appears in AstraID as a device you can remove).

## Building

    python3 tools/build.py --astra ../astra

The astraOS source tree provides `tools/apkgtool`. astraOS images bundle a copy
of Market (`apps/market` in the astra repository, refreshed with
`tools/market/update.py`).

Apache License 2.0.
