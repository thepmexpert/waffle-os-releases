# WaffleOS Downloads

Public download channel for **WaffleOS** release binaries. The source code lives in a private repository; this repo contains **only release artifacts** built and published automatically by CI.

## Install on Windows

1. Go to [Releases](https://github.com/thepmexpert/waffle-os-releases/releases/latest)
2. Download `WaffleOS-Setup-x64-v<version>.exe` — asset names carry the release version, e.g. `WaffleOS-Setup-x64-v0.1.4.exe`
3. Double-click, follow the wizard (SmartScreen may ask: choose **More info → Run anyway** — binaries are not code-signed yet)
4. The setup wizard asks a few questions and starts WaffleOS — a tray icon appears when it is running

No Python, no command line, no PATH edits required.

## Verify checksums

Every release ships a `SHA256SUMS` manifest:

```
sha256sum -c SHA256SUMS        # Linux / macOS
Get-FileHash -Algorithm SHA256 .\WaffleOS-Setup-x64-v<version>.exe   # PowerShell — replace <version> with the release you downloaded (e.g. v0.1.4)
```

## Notes

- Assets are attached to releases by CI from the private build repo on every `v*` tag.
- Questions or issues? Contact the maintainers (issues are disabled on this mirror repo).
