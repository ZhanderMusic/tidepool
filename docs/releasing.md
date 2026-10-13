# Releasing (maintainer notes)

Everything players get comes from `web/`. Every push to `main` runs **Build and release**:

1. The website (installable PWA) on GitHub Pages updates every time.
2. If `web/version.json` has a version with no release yet, GitHub builds the Windows installer and creates release `vX.Y.Z` with `Tidepool_X.Y.Z_x64-setup.exe` and `tidepool-web-vX.Y.Z.zip` (for itch.io, upload as an HTML game).

## Shipping a new version

- Bump the version in **both** `web/version.json` and `GAME_VERSION` in `web/index.html`. They must match or the build stops.
- Only bump the minor or patch number. Major versions (2.0.0) are for new seasons.
- Optional: add `release-notes/X.Y.Z.md` for the release page. Without it, `release-notes/_default.md` is used. Editing the notes file for the current version updates the existing release page.

## Layout

| Path | What it is |
| --- | --- |
| `web/index.html` | The game |
| `web/version.json` | Current version, also what the in-game update notice checks |
| `web/manifest.webmanifest`, `web/sw.js`, `web/icons/` | Installable app and offline play |
| `src-tauri/` | Windows app wrapper (Tauri) |
| `release-notes/` | Release page text |
| `.github/workflows/release.yml` | The automatic build |
