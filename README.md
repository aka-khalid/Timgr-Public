<div align="center">

<img src="Logo.png" alt="Timgr" width="96" height="96" />

# Timgr

**Turn a fingerprint attendance export into a payroll-ready timesheet.**

An offline Windows app. No account, no server, no telemetry.

<img alt="Windows 10 and 11, 64-bit" src="https://img.shields.io/badge/Windows-10%20%7C%2011%20x64-0078D4?logo=windows&logoColor=white"> <img alt="No network" src="https://img.shields.io/badge/network-none-2EA44F"> <img alt="Version 1.3.0" src="https://img.shields.io/badge/version-1.3.0-BE3144"> <img alt="Proprietary license" src="https://img.shields.io/badge/license-proprietary-6E7781">

**[Download for Windows](../../releases/latest)** &nbsp;·&nbsp; [Release notes](../../releases/latest) &nbsp;·&nbsp; [Licensing](#licensing)

<img src="screenshot-review.png" alt="Timgr's Review screen: 198 items found, 94 still needing an answer" width="100%" />

</div>

## What it does

| Step | What happens |
| --- | --- |
| **1. File** | Open the `.xls` or `.xlsx` export from the fingerprint device. |
| **2. Review** | Duplicate taps are merged, punches are paired into shifts, and anything odd is put in front of you instead of being guessed at. |
| **3. Pay period** | The pay period, working hours, overtime, days off, and the pay rules for that period. |
| **4. Export** | An Excel file in the layout payroll already expects. |

<p align="center">
  <img src="screenshot-file.png" alt="The File screen after loading an export: 877 attendance rows, 14 employees, 198 items to review, 104 fixed automatically" width="100%" />
  <br />
  <sub>One export loaded: 877 rows, 14 employees, 193 duplicate taps merged, 104 items fixed on their own, 198 left to answer.</sub>
</p>

The file is read on the PC and the workbook is written on the PC. Nothing is uploaded.

## Download

**[Timgr 1.3.0 for Windows](../../releases/latest)** is the current build: one installer, about 5 MB, for Windows 10 and 11 on 64-bit.

Check the file before you run it. The release also carries `SHA256SUMS.txt` with the same hash.

```powershell
Get-FileHash .\Timgr_1.3.0_x64-setup.exe -Algorithm SHA256
```

The result must be:

```text
AFF52823E20448064032910DF6793C433A04231F9DBF5BBF2BFAEE42302AD875
```

## Install

1. Run `Timgr_1.3.0_x64-setup.exe`.
2. Windows SmartScreen shows **"Windows protected your PC"** because the installer is not code-signed yet. Choose **More info**, then **Run anyway**.
3. It installs for the current Windows user, with a Start-menu shortcut. No admin prompt.

Needs Windows 10 (1809 or newer) or Windows 11, 64-bit, and about 200 MB of disk. Most of that space is Microsoft's WebView2 runtime; Windows 11 and updated Windows 10 already have it, and the installer only downloads it when it is missing.

Installing a newer version over an older one keeps your settings, drafts, and export history.

## Licensing

Saving a workbook needs a license: one small signed file, checked on this PC, never sent anywhere.

1. Open **License** in the app. If the license will be tied to this PC, copy the **Device code** shown there.
2. Send that code to whoever issues your license.
3. Import the `.timgr-license` file you get back, or paste its text. The screen then reads **This device is licensed**.

The interface is in English and Arabic, with full right-to-left layout.

## What's new in 1.3.0

- **A signing key no longer needs a new installer.** The app carries a root key that can authorize a daily signing key, so keys can be rotated without shipping a new build.
- **Delegated licenses say so.** A license signed by a delegated key shows **ISSUED UNDER** with the root that authorized it.
- **Damage is named.** An edited delegation reads "This license is damaged or was changed"; a missing or repeated one reads "This license's signing chain is not valid". A failed import never replaces the license already on the machine.

The review screen, the pipeline, and the saved workbook are unchanged from 1.2.x. Full notes are on the [release page](../../releases/latest).

## Privacy

- No account, no sign-in, no telemetry, no crash reporting.
- The attendance file never leaves the PC, and the app makes no network requests.
- The only network use anywhere is the installer fetching WebView2 when Windows is missing it.
- Data lives in `%APPDATA%\com.timgr.desktop`: settings, drafts, export history, the installed license. Delete that folder to remove it.

## Uninstall

Windows **Settings > Apps > Timgr > Uninstall**, or the Start-menu uninstaller. Drafts and history in `%APPDATA%\com.timgr.desktop` are kept; delete that folder to remove them too.

## Older versions

The **v2.5.x** releases are the earlier Python version of Timgr, kept for reference. The current app is the Windows installer above and is a different program: no Python, nothing to install first.

## License

This software is proprietary. Unauthorized copying, modification, or distribution is prohibited. For licensing questions, contact the development team.

---

<sub>Last updated November 2026. Found a problem? Open an issue.</sub>
