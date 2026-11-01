# Timgr

<img src="Logo.png" alt="Timgr logo" width="110" />

[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011%20x64-blue)](#requirements)
[![Offline](https://img.shields.io/badge/Network-none-success)](#privacy)
[![License](https://img.shields.io/badge/License-Proprietary-red)](#license)

**Timgr** turns a fingerprint-device attendance export into a reviewed,
period-based timesheet workbook. Pick the export, review what the app flagged,
set the pay period and the pay rules, and save an Excel file that is ready for
payroll.

Everything runs on your own PC. There is no account, no server, no telemetry,
and the app makes no network requests.

---

## Download

Take the current build from **[Releases](../../releases/latest)**.

| File | Version | Size | SHA-256 |
| --- | --- | --- | --- |
| `Timgr_1.3.0_x64-setup.exe` | 1.3.0 | 5,456,463 bytes (5.20 MiB) | `AFF52823E20448064032910DF6793C433A04231F9DBF5BBF2BFAEE42302AD875` |

`SHA256SUMS.txt` is attached to the same release. Check the file before you run
it:

```powershell
Get-FileHash .\Timgr_1.3.0_x64-setup.exe -Algorithm SHA256
```

The result must match the hash above.

## Requirements

- Windows 10 (1809 or newer) or Windows 11, 64-bit.
- Microsoft Edge WebView2. Windows 11 and any updated Windows 10 already have
  it. The installer downloads it only if it is missing, so a machine without
  WebView2 needs internet once.
- About 200 MB free disk space. The app itself is small; most of that is the
  WebView2 runtime.
- No administrator rights. The app installs for the current Windows user.

## Install

1. Run `Timgr_1.3.0_x64-setup.exe`.
2. Windows SmartScreen shows **"Windows protected your PC"** because the
   installer is not code-signed. Choose **More info**, then **Run anyway**.
3. The app installs for the current user and adds a Start-menu shortcut.

Installing a newer version over an older one keeps your settings, drafts and
export history.

## First run and licensing

Saving an Excel file needs a license. The license is a small signed file that
is checked offline on this PC; nothing about it is sent anywhere.

1. Open **License** in the app. If your license is tied to one PC, copy the
   **Device code** shown there and send it to whoever issues your license.
2. Import the `.timgr-license` file you were sent, or paste its text.
3. The screen reads **This device is licensed**.

The app has an English and an Arabic interface, including right-to-left layout.

## What's new in 1.3.0

- **A signing key can be authorized without rebuilding the app.** The app now
  carries a root key that can delegate a daily signing key, so a new key can be
  issued and used without shipping a new installer.
- **Delegated licenses say so.** A license signed by a delegated key shows
  **ISSUED UNDER** with the root that authorized it.
- **Damage is named.** An edited delegation reads "This license is damaged or
  was changed"; a missing or repeated one reads "This license's signing chain
  is not valid". A failed import never replaces the license already installed.

The full notes are in the release description. The app's pipeline, review
screen and workbook output are unchanged from the previous build.

## Verifying a release

Each release lists the SHA-256 of the installer and attaches `SHA256SUMS.txt`.
Verify the hash before installing, especially if the file came through email or
a chat app.

## Privacy

- No account, no sign-in, no telemetry, no crash reporting.
- The attendance file is read on your PC and never uploaded.
- The app makes no network requests. The only network use anywhere is the
  installer fetching WebView2 when Windows is missing it.
- Data lives in `%APPDATA%\com.timgr.desktop` (settings, drafts, export history,
  the installed license). Delete that folder to remove it.

## Uninstall

Windows **Settings > Apps > Timgr > Uninstall**, or the Start-menu uninstaller.
Drafts and history in `%APPDATA%\com.timgr.desktop` are kept; delete that folder
to remove them too.

## Older versions

The **v2.5.x** releases are the earlier Python version of Timgr. They are kept
for reference. The current app is the Windows installer listed above, and it is
a different program: no Python, no dependencies to install.

## License

This software is proprietary. Unauthorized copying, modification or
distribution is prohibited. For licensing questions, contact the development
team.

---

*Last updated: November 2026*
