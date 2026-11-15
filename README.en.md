# Kirara_Server_Studio

<p align="center">
  <img src="https://img.shields.io/badge/Version-1.7.1-blue" alt="Version">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2B-0078D4" alt="Platform">
  <img src="https://img.shields.io/badge/.NET-10-512BD4" alt=".NET">
  <img src="https://img.shields.io/badge/License-All%20Rights%20Reserved-lightgrey" alt="License">
</p>

<p align="center"><a href="README.md">简体中文</a> | English</p>

**The Windows client for Kirara_Server.** It brings the services you use on Kirara_Server — media library, cloud drive, live streaming, mail, remote desktop, OpenVPN, game servers — into a single window. Instances keep accounts and purposes apart; link a token once and every page signs itself in.

---

## What it does

| Capability | What you get |
| --- | --- |
| **Instances** | Create one instance per account or per purpose, fully isolated from each other. Rename, pin or colour-tag them, and export one as a `.kirara` file to share. |
| **20+ built-in schemes** | Media, cloud drive, live streaming, mail, notes, community, remote desktop, OpenVPN, virtualisation and router firmware, game servers, certificates and more. A third-party executable can also be loaded as a scheme. |
| **Automatic sign-in** | Tokens are encrypted on disk. Opening an instance signs you in to each service; server restarts and network hiccups are retried instead of being mistaken for an invalid token. |
| **Token manager** | Keeps accounts and credentials in one place and exports them to your phone as a QR code. The code refreshes every 15 seconds and only the owning account can import it. |
| **App store** | One-click install or upgrade of FreeRDP, OpenVPN and WebView2. In-app downloads go through the download manager, with pause, resume and stop. |
| **Notifications and community** | Live notifications, issue comments, favourites and update requests, synced with the mobile app. Notifications can carry image and video cards. |
| **Cloud sync** | Back up instances and tokens and restore them on another machine. Local preferences and notification read states stay out of the sync and are never overwritten by a restore. |
| **Desktop fit and finish** | Fluent 2 UI, light/dark mode with 48 accent colours, start with Windows, and files dragged straight into a page. |

## Requirements

| Item | Requirement |
| --- | --- |
| OS | Windows 10 1809 (10.0.17763) or later; Windows 11 recommended |
| Architecture | x64 |
| Memory | 16 GB recommended |
| GPU | NVIDIA GeForce RTX 2060 or better with current drivers (used for AI upscaling and HDR) |
| Runtime | .NET 10, bundled with the installer |
| Privileges | No admin rights for daily use; installing, upgrading and uninstalling do need them |

## Download and install

1. Download the latest `Kirara_Server_Studio_Setup_x64_vX.X.X.exe` from **Releases**.
2. Run the installer. WebView2 is required; OpenVPN and FreeRDP are optional, unchecked by default, and can be added later from the in-app **App Store**.
3. Sign in with your Kirara_Server passport and accept the Kirara Server Studio Software License Agreement.
4. Updates are handled by the built-in updater. If you skipped several releases, the notes are listed release by release; a release marked as important must be installed before you can continue.

## Quick start

```
(1) Create instance  ->  (2) Pick schemes  ->  (3) Link token
```

1. **Create an instance** — in the left sidebar choose "Create user instance" or "Create service instance" and give it a name. First time around you can also apply a template from **Quick Start**.
2. **Pick schemes** — tick the services you want; multiple choices are allowed.
3. **Link a token** — create the matching token in the **Token manager**, then link it on the scheme page. Once deployment finishes, each page signs itself in.

After that, opening the instance takes you straight in. The mobile app [Kirara_Media](https://gitee.com/kiraramoe/kirara_media) can import the same token: **Settings → Token manager → Scan to import**, pointed at the QR code on the desktop.

## Everyday controls

- **Close an instance** — the "Close instance" button on the instance tab; it greys out while the instance is busy or not running.
- **Cloud sync** — the cloud button next to the search box in the left sidebar, or the one in the token manager.
- **Plugins** — **App Store** at the top of the left navigation installs, upgrades and removes FreeRDP / OpenVPN / WebView2.
- **Notifications** — the badge in the bottom-right corner opens a panel with Feed / Services / Log tabs.
- **Data and appearance** — **Settings** covers cache, local data, cloud data and themes.

## FAQ

<details>
<summary><b>Do I need admin rights to install or to use the VPN?</b></summary>

Not for daily use. The app runs as a normal user (`asInvoker`); the TAP / Wintun adapter OpenVPN needs is created by the `KiraraVpnHelper` service (LocalSystem) registered at install time, so connecting a VPN never raises a UAC prompt. Only installing, upgrading and uninstalling the package itself need administrator rights.
</details>

<details>
<summary><b>Scanning the QR code on my phone fails.</b></summary>

The desktop app and the phone must be signed in to the same Kirara account — a token can only be imported by the account that owns it. The code refreshes roughly every 15 seconds; if it reports "QR code expired", wait for the next refresh, scan immediately, and keep the desktop dialog open.
</details>

<details>
<summary><b>Does cloud sync upload my settings and notifications?</b></summary>

No. Sync covers instances and tokens only; theme, behaviour, sidebar preferences and notification read states are excluded, and any such fields carried by an older backup are ignored on restore. Stored cloud data can be deleted under **Settings → Data management → Clear cloud data**.
</details>

<details>
<summary><b>Where is my data, and how do I start over?</b></summary>

Data lives under `%APPDATA%\Kirara\`, split per account, with tokens and other secrets encrypted — don't copy the folder to someone else. **Settings → Data management** offers "Clear cache" and "Clear local data"; the latter also removes the remembered accounts on the sign-in page and the start-with-Windows entry, cannot be undone, and is best preceded by exporting your instances and tokens.
</details>

<details>
<summary><b>It says a plugin is missing or out of date.</b></summary>

Open **App Store**, search for the plugin and install or upgrade it; readiness is detected automatically. Debug builds only reuse installed components and never install or remove them — use a release build to install.
</details>

<details>
<summary><b>Does it work offline?</b></summary>

Yes, within limits. Scheme pages fall back to local cache, and remote services such as authentication and comments degrade to local data. Once the network is back, online sync and live push resume automatically.
</details>

## Documentation

- [Technical documentation (Chinese)](docs/技术栈文档.md)
- [Software license agreement (Chinese)](docs/软件许可协议.md)
- Mobile client: [Kirara_Media](https://gitee.com/kiraramoe/kirara_media)

## License

This is closed-source proprietary software. All rights reserved. Use is subject to the Kirara Server Studio Software License Agreement; the copy shown inside the app is authoritative (identical to [docs/软件许可协议.md](docs/软件许可协议.md)), and the English translation is available in [LICENSE](LICENSE) and [docs/软件许可协议.en.md](docs/软件许可协议.en.md).

Decompiling, redistributing, modifying or republishing the software without authorization is prohibited. Third-party open-source components remain the property of their respective authors.

## Credits

- [LiteDB](https://github.com/litedb-org/LiteDB)
- [OpenVPN](https://github.com/OpenVPN)
- [FreeRDP](https://github.com/FreeRDP)
- [QRCoder](https://github.com/codebude/QRCoder)

---

<p align="center">Made with ❤ by SenVenth</p>
