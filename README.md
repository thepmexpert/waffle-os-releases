# WaffleOS Downloads

Public download channel for **WaffleOS** release binaries. The source code lives in a private repository; this repo contains **only release artifacts** built and published automatically by CI.

## Install on Windows

1. Download [`WaffleOS-Setup-x64.exe`](https://github.com/thepmexpert/waffle-os-releases/releases/latest/download/WaffleOS-Setup-x64.exe) — always the latest release
2. Double-click, follow the wizard (SmartScreen may ask: choose **More info → Run anyway** — binaries are not code-signed yet)
3. The setup wizard asks a few questions and starts WaffleOS — a tray icon appears when it is running

No Python, no command line, no PATH edits required.

## Other downloads

- Windows portable (tray + CLI, no installer): [`WaffleOS-windows-x64.zip`](https://github.com/thepmexpert/waffle-os-releases/releases/latest/download/WaffleOS-windows-x64.zip)
- macOS (Apple Silicon): [`WaffleOS-macos-arm64.dmg`](https://github.com/thepmexpert/waffle-os-releases/releases/latest/download/WaffleOS-macos-arm64.dmg)
- macOS / Linux CLI: the `waffle-*` assets on the [latest release](https://github.com/thepmexpert/waffle-os-releases/releases/latest)

## Verify checksums

Every release ships a `SHA256SUMS` manifest:

```
sha256sum -c SHA256SUMS        # Linux / macOS
Get-FileHash -Algorithm SHA256 .\WaffleOS-Setup-x64.exe   # PowerShell
```

## Notes

- Asset names are evergreen (no version in the filename): every release ships the same names, so the links above always resolve to the latest release. Earlier releases keep their own assets under their own tags.
- The version of a downloaded file is stamped inside it (Add/Remove Programs entry, DMG Info.plist) and listed per release in `SHA256SUMS`.
- Assets are attached to releases by CI from the private build repo on every `v*` tag.
- Questions or issues? Contact the maintainers (issues are disabled on this mirror repo).
