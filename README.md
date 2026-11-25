# VyskGrid Host

**VyskGrid is a community compute network.** People with spare computing capacity (**hosts**) lend their idle
graphics card and processor to run batch jobs for people who need them (**tenants**). The **VyskGrid Host app** is the
program a host installs. It sits in the system tray, runs jobs only inside locked-down containers, and only when the
host's own limits allow.

> **Status: closed beta, test mode.** No real money is charged, held or paid. Earnings and payouts are practice
> figures. The app is **not code-signed yet**, so Windows SmartScreen will warn you (see "Install").

This repository contains **only releases and documentation**. The source code is not published. See [LICENSE](LICENSE).

## Download

| Platform | Status |
| --- | --- |
| **Windows 11 (64-bit)** | [Download v0.3.0 from Releases](../../releases/tag/v0.3.0) |
| macOS | Not available yet |
| Linux | Not available yet |

Also available from the website: <https://grid.vyskatech.com/download.html>. Both places carry the same file and the
same checksum.

## Requirements

- Windows 11, 64-bit.
- **Docker Desktop** (WSL 2 mode) installed and running. Jobs run in containers.
- For GPU jobs: an NVIDIA graphics card with a current driver. (Tested so far on one machine: Windows 11, Docker
  Desktop, GeForce RTX 3060. Other cards are untested.) CPU-only jobs need no graphics card.
- A stable internet connection. The app only makes outgoing connections and opens no ports.
- An account at <https://grid.vyskatech.com/app/> to get a one-time connection token (Share a computer page).

## Verify your download

Each release lists a SHA-256 checksum, and `SHA256SUMS.txt` is attached. In PowerShell:

```powershell
certutil -hashfile VyskGrid-Host_<version>_x64-setup.exe SHA256
```

The value must be identical to the one published. If it is not, delete the file and do not run it.

## Install

1. Run the installer. Because it is not code-signed yet, Windows SmartScreen shows "Windows protected your PC".
   After you have checked the checksum above, choose **More info**, then **Run anyway**.
2. Open **VyskGrid Host**. In **Connect this computer**, the platform addresses are already filled in. Paste the one-time
   token from your account, connect, then start sharing.
3. Closing the window keeps sharing running in the **system tray**. Use the tray icon and **Quit** to stop. You can
   also tick **Start when I sign in** to have it start hidden in the tray.

## Your limits always win

Pause at any time, set a weekly schedule, and set a graphics-card temperature limit. These are stored on your
computer; the platform cannot change them. No new job starts while you are paused, outside your schedule, or too hot.

## What runs on your computer

Only container images whose exact digest the VyskGrid owner has signed, started by the app itself. Each job runs as an
unprivileged user with a read-only filesystem, no network, hard limits on memory, processes, run time and output, and
only the graphics card assigned to it. **No sandbox is perfect**: containers share your computer's kernel. Read the
[Safety page](https://grid.vyskatech.com/security.html) and the
[Host Agreement](https://grid.vyskatech.com/host-agreement.html) before you decide to share a computer.

## Support and security

- Help: <support@vyskatech.com>
- Report a security problem: <security@vyskatech.com> (see [SECURITY.md](SECURITY.md))
- Privacy and legal: <https://grid.vyskatech.com/privacy.html>, <https://grid.vyskatech.com/terms.html>

## Licence

Proprietary. All rights reserved. You may download and use the released program under the
[Terms of Service](https://grid.vyskatech.com/terms.html). See [LICENSE](LICENSE).
