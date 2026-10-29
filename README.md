# GM-CTRL Releases

This repository hosts the Windows installer releases for **GM-CTRL-MASTER** —
the Escape Room Game Master Control Panel desktop app from
[gmctrl.com](https://www.gmctrl.com).

It exists separately from the (private) source repository so that the
auto-update channel works without authentication.

## Download the latest installer

Grab the latest `GM-CTRL-MASTER-Setup-X.Y.Z.exe` from the
[**Releases page**](https://github.com/X04N/gm-ctrl-releases/releases/latest).

After install, GM-CTRL-MASTER keeps itself up-to-date automatically — every
release published here triggers an in-app notification with a one-click
"Install Now" button.

## Each release contains

| File | What it is |
|---|---|
| `GM-CTRL-MASTER-Setup-X.Y.Z.exe` | Signed installer for Windows x64 (install, update and uninstall) |
| `latest.yml` | Manifest used by `electron-updater` — contains the SHA-512 of the .exe for integrity verification |

Since v0.24.0 there is no `.blockmap`: updates always download the full
installer.

## Verifying the installer

The installer is signed by **Joan Casas Vidal** (right-click the .exe →
Properties → Digital Signatures).

Each release's `latest.yml` includes a base64 SHA-512 hash of the installer.
The auto-updater verifies it automatically. To verify manually:

```powershell
$bytes = [IO.File]::ReadAllBytes("GM-CTRL-MASTER-Setup-X.Y.Z.exe")
[Convert]::ToBase64String([Security.Cryptography.SHA512]::Create().ComputeHash($bytes))
# Compare against the `sha512` field in latest.yml
```

## Reporting issues

This repo doesn't accept issues — file bug reports through the in-app
**Report a bug** button (sidebar or footer chip), or email
[bugs@gmctrl.com](mailto:bugs@gmctrl.com).
