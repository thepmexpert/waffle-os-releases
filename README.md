# WaffleOS Downloads

Public download channel for **WaffleOS** release binaries. The source code lives in a private repository; this repo contains **only release artifacts** built and published automatically by CI.

## Install on Windows

1. Go to [Releases](https://github.com/thepmexpert/waffle-os-releases/releases/latest)
2. Download `WaffleOS-Setup-x64-v0.1.24.exe`
3. Double-click, follow the installer (SmartScreen may ask: choose **More info → Run anyway** — binaries are not code-signed yet)
4. Setup installs WaffleOS and the tray icon appears. Open **Settings** from the tray: set an LLM base URL, connect at least one channel (Slack, Teams, Paperclip, or OpenClaw), then **Save changes** — that starts WaffleOS. Until then WaffleOS does not start its server.

No Python, no command line, no PATH edits required.

## Verify checksums

Every release ships a `SHA256SUMS` manifest:

```
sha256sum -c SHA256SUMS        # Linux / macOS
Get-FileHash -Algorithm SHA256 .\WaffleOS-Setup-x64-v0.1.24.exe   # PowerShell
```

## Notes

- Assets are attached to releases by CI from the private build repo on every `v*` tag.
- Questions or issues? Contact the maintainers (issues are disabled on this mirror repo).
