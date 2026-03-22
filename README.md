<div align="center">

# 🎵 Spotigrate

**Migrate your Spotify Liked Songs into any playlist. Delete songs from any playlist.**  
A desktop automation app built with Python, Playwright, and CustomTkinter.

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=flat-square&logo=python&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D4?style=flat-square&logo=windows&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-1DB954?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-1DB954?style=flat-square)

</div>

---

## What is Spotigrate?

Spotigrate automates the tedious task of managing your Spotify library. It connects to the Spotify web player running inside Google Chrome and lets you:

- **Migrate** every song from your Liked Songs into a named playlist — or hand-pick exactly which ones
- **Delete** specific songs from any playlist via a clean searchable checklist
- Watch everything happen in a **live colour-coded log** with a real-time progress bar

No Spotify API credentials needed. No OAuth setup. Just Chrome and Spotify.

---

## Features

| Feature | Description |
|---|---|
| ⚡ One-click Chrome Launch | Opens Chrome with the debugging port pre-configured — no terminal needed |
| 🎵 Migrate All Songs | Moves your entire Liked Songs library into any playlist automatically |
| 🎯 Pick & Choose | Fetches your library, then lets you tick exactly which songs to migrate |
| 🗑 Delete from Playlist | Load any playlist by URL and remove selected songs |
| 📊 Live Progress Bar | Real-time counter showing X / Total (XX%) during every operation |
| 🌈 Colour-coded Log | Green = added, Yellow = warning, Red = error — at a glance status |
| 👁 Preview Mode | Dry-run scan of your Liked Songs without migrating anything |
| ⏹ Stop Button | Safely halts any running operation after the current song finishes |
| 🔗 Chrome Status Indicator | Live badge showing connection state, auto-refreshes every 5 seconds |
| 📋 Copy Log | One-click copy of the full activity log to clipboard |
| 🔐 Account System | Gmail + Password + License Key auth with encrypted local storage |
| 🚀 Auto-Login | Remembers your session — next launch goes straight to the app |

---

## Screenshots

<img width="1915" height="996" alt="image" src="https://github.com/user-attachments/assets/21c4cffb-f547-4d9a-8e01-4de91c20aad0" />

---

## Installation

### Download the EXE (recommended)

1. [Download Spotigrate.exe from Google Drive](https://drive.google.com/file/d/1NcpwfdnSweziVNB4kVsxEM6Ih80M9XPY/view?usp=sharing)
2. Double-click to run — no Python or dependencies required

> Windows may show a "Windows protected your PC" popup. Click **More info → Run anyway**. This is normal for unsigned applications.

---

## Quick Start

### 1. Launch the app

Double-click `Spotigrate.exe` (or run `python spotigrate_auth.py` from source).

### 2. Create an account

On first launch, the **Register** screen appears:
- Enter your Gmail address and a password (min. 6 characters)
- Click **Create Account**
- A unique **License Key** is generated for you — copy it and save it somewhere safe
- Click **Continue to Login**

### 3. Log in

Enter your Gmail, password, and the License Key you were given. Click **Log In**.  
After the first successful login, the app remembers you and opens automatically on future launches.

### 4. Connect Chrome

Click the green **⚡ Launch Chrome** button in the app. Then:
- Open `open.spotify.com` in that Chrome window
- Log in to Spotify if prompted
- The status badge in the top-right turns green: `Chrome connected · 1 Spotify tab(s)`

### 5. Migrate or Delete

**To migrate Liked Songs:**
1. Go to the **Migrate** tab (selected by default)
2. Type the exact name of a playlist you own in Spotify
3. Choose **All Songs** or **Pick & Choose** mode
4. Click **Start Migration**

**To delete from a playlist:**
1. Click the **Delete** tab
2. Paste the playlist's Spotify URL and type its name
3. Click **Load Songs** — a picker window opens
4. Tick the songs to remove and click **Delete Selected**

---

## Auth System

Spotigrate includes a local account system — no server, no internet required for auth.

```
Register  →  Gmail + Password  →  License Key generated & shown
Login     →  Gmail + Password + License Key  →  App opens
Next run  →  Auto-login (no screen shown)
Logout    →  Clears session, shows login on next launch
```

**All data is stored encrypted on your PC at:**
```
%APPDATA%\Spotigrate\
```

| File | Purpose |
|---|---|
| `users.dat` | Encrypted user database (Gmail, hashed password, license key) |
| `session.dat` | Current login session (encrypted) |
| `.fkey` | Local encryption key (hidden file) |

> ⚠️ If you lose your License Key, there is no recovery. Save it in a password manager or note app when you register.

---

## How it Works

Spotigrate uses **Playwright** to connect to a Google Chrome instance running with a remote debugging port. It reads and interacts with the Spotify web player exactly as a human would — scrolling through your library, right-clicking songs, and selecting playlists from the context menu.

```
Spotigrate ──(CDP)──► Chrome ──(web)──► Spotify
```

No Spotify API keys. No rate-limit tokens. No OAuth. Just browser automation.

---

## Tech Stack

| Library | Purpose |
|---|---|
| [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) | Modern dark-themed GUI framework |
| [Playwright](https://playwright.dev/python/) | Browser automation (Chrome DevTools Protocol) |
| [cryptography](https://cryptography.io/) | Fernet encryption for local auth storage |
| tkinter | Scrollable lists, dialogs, log widget |
| asyncio + threading | Non-blocking background operations |

---

## Known Limitations

- **Windows only** for the EXE. Running from Python source works on macOS and Linux.
- Requires **Google Chrome** — Firefox and Edge are not supported.
- Spotify's web player UI changes occasionally and may break selectors — update the app if this happens.
- Very large libraries (5000+ songs) can take a long time at default pause settings. Use Pick & Choose to migrate in batches.
- The License Key cannot be recovered if lost — store it safely after registering.

---

## FAQ

**Do I need a Spotify Premium account?**  
No. Spotigrate works with both Free and Premium accounts.

**Does Spotigrate store my Spotify password?**  
No. Spotigrate only stores the password you choose during registration (not your Spotify password). It connects to Chrome which already has Spotify open — no Spotify credentials are ever seen or stored by the app.

**Can I share the EXE with a friend?**  
Yes. Just share the single `Spotigrate.exe` file. When they run it on their PC, they register their own account. Each PC has its own separate user database.

**Is my data sent anywhere?**  
No. Auth is entirely local. Internet is only used by Spotify itself loading in Chrome.

**What if migration gets interrupted?**  
Re-run it. Songs already in the playlist are automatically skipped, so only remaining songs will be processed.

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m 'Add my feature'`
4. Push: `git push origin feature/my-feature`
5. Open a Pull Request

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Contact

For any questions or issues, please contact:

- **Email**: [Click to here send email](https://mail.google.com/mail/?view=cm&fs=1&to=shukdevdatta@gmail.com)
- **GitHub**: [Click to here to access the Github Profile](https://github.com/shukdevtroy)
- **WhatsApp**: [Click here to chat](https://wa.me/+8801719296601)
- **HuggingFace Profile**: [Click to here to access the HuggingFace Profile](https://huggingface.co/shukdevdatta123))
- **HuggingFace Profile**: [Click to here to access the 2nd HuggingFace Profile](https://huggingface.co/shukdevdattaEX))
- **HuggingFace Profile**: [Click to here to access the 3rd HuggingFace Profile](https://huggingface.co/shukdev3))

---
