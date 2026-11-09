# WaffleOS Downloads

Public download channel for **WaffleOS** release binaries. The source code lives in a private repository; this repo contains **only release artifacts** built and published automatically by CI.

## Install on Windows

1. Go to [Releases](https://github.com/thepmexpert/waffle-os-releases/releases/latest)
2. Download `WaffleOS-Setup-x64-v0.1.9.exe`
3. Double-click, follow the wizard (SmartScreen may ask: choose **More info → Run anyway** — binaries are not code-signed yet)
4. The setup wizard asks a few questions and starts WaffleOS — a tray icon appears when it is running

No Python, no command line, no PATH edits required.

## Install on macOS / Linux (manual)

1. Go to [Releases](https://github.com/thepmexpert/waffle-os-releases/releases/latest) and download the archive for your machine, plus the `SHA256SUMS` manifest from the same release:
   - Apple Silicon Mac: `waffle-macos-arm64.tar.gz`
   - Intel Mac: `waffle-macos-amd64.tar.gz`
   - Linux x86-64: `waffle-linux-amd64`
2. Verify the checksum (the line must end in `OK`):
   ```bash
   grep waffle-macos-arm64 SHA256SUMS | shasum -a 256 -c -   # macOS
   grep waffle-linux-amd64  SHA256SUMS | sha256sum -c -      # Linux
   ```
3. Extract and run:
   ```bash
   tar -xzf waffle-macos-arm64.tar.gz && ./waffle --help
   ```
4. Create a vault and start the daemon (always pass an explicit `--root` — the binary refuses to run against the vault bundled inside it):
   ```bash
   ./waffle --root ~/waffle-vault init-root
   printf 'WAFFLE_DAEMON_TOKEN=%s\n' "$(openssl rand -hex 32)" > ~/waffle-vault/.env.local
   ./waffle --root ~/waffle-vault serve   # daemon on 127.0.0.1:8787
   curl http://127.0.0.1:8787/healthz     # {"ok":true,...} = up
   ```

### macOS Gatekeeper note

The macOS binaries are ad-hoc signed and not notarized yet, so on Apple Silicon Gatekeeper silently blocks a downloaded binary launched from Finder or `open`. After verifying the checksum, use one of these for the first launch — afterwards the binary starts normally:

- run it from Terminal (`./waffle ...`), or
- `xattr -d com.apple.quarantine ./waffle`, or
- right-click the binary in Finder → **Open** → **Open** on the warning.

## Verify checksums

Every release ships a `SHA256SUMS` manifest:

```
sha256sum -c SHA256SUMS        # Linux / macOS
Get-FileHash -Algorithm SHA256 .\WaffleOS-Setup-x64-v0.1.9.exe   # PowerShell
```

## Notes

- Assets are attached to releases by CI from the private build repo on every `v*` tag.
- The resident tray app is currently **Windows-only**; macOS/Linux installs run the `waffle` CLI/daemon without a tray icon.
- Questions or issues? Contact the maintainers (issues are disabled on this mirror repo).
