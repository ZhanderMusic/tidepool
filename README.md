# Tidepool

A calm idle game about growing a tide pool.

- **Play / install on your phone:** https://zhandermusic.github.io/tidepool/
- **Windows app and downloads:** [Releases](https://github.com/ZhanderMusic/tidepool/releases)

## How releases work

Everything comes from the `web/` folder. Pushing to `main` runs the **Build and release** workflow:

1. The website (the installable PWA) updates on GitHub Pages every time.
2. If `web/version.json` has a version with no release yet, GitHub also builds the Windows installer and creates a release `vX.Y.Z` with:
   - `Tidepool_X.Y.Z_x64-setup.exe` (Windows)
   - `tidepool-web-vX.Y.Z.zip` (upload to itch.io as an HTML game)

### Shipping a new version

Bump the version in **both** places, which must match (the build stops if they don't):

- `web/version.json`
- `GAME_VERSION` near the top of the script in `web/index.html`

Version rule: only bump the minor or patch number (1.5.0 → 1.6.0 or 1.5.1). The major number (2.0.0) is reserved for new seasons.

Players see an in-game "new version available" notice after a release: web and phone players just reload, and the desktop app links to the latest release.

## Files

| Path | What it is |
| --- | --- |
| `web/index.html` | The game |
| `web/version.json` | Current version, also what the update notice checks |
| `web/manifest.webmanifest`, `web/sw.js`, `web/icons/` | Makes it installable and playable offline |
| `src-tauri/` | Windows app wrapper (Tauri) |
| `.github/workflows/release.yml` | The automatic build |
