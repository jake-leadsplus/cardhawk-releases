<div align="center">

# 🦅 CardHawk

### Catch the drop before the bots do.

**A personal-use restock watcher + one-tap checkout assistant for Pokémon TCG drops on Target.**
Runs in *your own* logged-in browser. No proxies, no fake accounts, no CAPTCHA-defeating — just your session, faster.

<br/>

[![Latest release](https://img.shields.io/github/v/release/jake-leadsplus/cardhawk-releases?style=for-the-badge&label=Download&labelColor=0b1021&color=7c3aed&logo=github)](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/jake-leadsplus/cardhawk-releases/total?style=for-the-badge&labelColor=0b1021&color=ec4899&logo=icloud&logoColor=white)](https://github.com/jake-leadsplus/cardhawk-releases/releases)
[![Release date](https://img.shields.io/github/release-date/jake-leadsplus/cardhawk-releases?style=for-the-badge&labelColor=0b1021&color=06b6d4)](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)

![Windows](https://img.shields.io/badge/Windows-silent_auto--update-0078D6?style=flat-square&logo=windows11&logoColor=white)
![macOS](https://img.shields.io/badge/macOS-Apple_Silicon-000000?style=flat-square&logo=apple&logoColor=white)
![Phone](https://img.shields.io/badge/Control_from_your-📱_phone-22c55e?style=flat-square)
![No bots](https://img.shields.io/badge/Anti--scalper-by_design-f59e0b?style=flat-square)

</div>

---

<div align="center">

### ⚡ [**Download the latest version →**](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)

</div>

| Platform | What to grab | Install |
|---|---|---|
| 🪟 **Windows 10/11** | the **`.exe`** installer | Run it. Done. Updates apply themselves, silently, in the background. |
| 🍎 **macOS (Apple Silicon)** | the **`-arm64.dmg`** | Open the `.dmg`, drag the app to **Applications**. First launch: **right-click → Open** (see [Gatekeeper note](#-macos-first-launch-gatekeeper)). |

> 💡 Not sure which? On Windows take the `.exe`. On a modern Mac (M1/M2/M3/M4) take the `-arm64.dmg`.

---

## 🎯 What CardHawk does

Drops sell out in **seconds** because scalper bots see the restock before a human ever refreshes the page. CardHawk closes that gap for a *regular buyer* — without becoming a bot.

<table>
<tr>
<td width="50%" valign="top">

### 👀 Watch
A read-only monitor polls the retailer's availability API and catches the **`OUT_OF_STOCK → IN_STOCK`** flip in **seconds** — not the 5–30 minutes a "notify me" email takes.

It polls *through your real browser session*, so it looks exactly like normal browsing. No separate footprint to flag.

</td>
<td width="50%" valign="top">

### 🛒 Buy
The instant stock appears, CardHawk drives the checkout in **your own logged-in tab**: add to cart → push through checkout → place the order, with an optional CVV confirm.

You stay in control — **arm**, **pause**, or approve each buy. Nothing happens unless you've armed it.

</td>
</tr>
</table>

---

## ✨ Highlights

- 🦅 **Seconds-fast restock detection** — sub-second polling cadence on a warm, real session.
- 🔒 **Runs in *your* browser** — your login, your card, your IP. No proxies, no throwaway browsers, no identity rotation.
- 🧢 **Hard 2-item cap** — quantity is clamped to **≤ 2** per drop, every path. Built to give a real fan a fair shot, *not* to enable resellers.
- 🛡️ **Safe by default** — nothing buys until you **arm** it; an unreadable order total **refuses** to place rather than guess.
- 📱 **Control it from your phone** — a built-in dashboard mirrors everything over your home Wi-Fi. Arm, pause, change price caps, add SKUs — from the couch.
- 🎯 **Watch your whole hit-list** — many Target SKUs at once, each with its own price cap. *(Amazon support is on the way.)*
- 🔁 **Auto-updates** — Windows updates silently; macOS gives you a one-tap assisted update. Your watch list, settings, and templates are **never touched** by an update.
- ⚡ **Buy-now for fresh drops** — snipe a SKU that dropped *already in stock*, not just on a restock flip.

---

## 🚀 Quick start

1. **Download & install** from the table above.
2. **Open CardHawk.** On first run it opens a Chrome window for you.
3. **Log in** to `target.com` in that window and save your card. (One time — it's remembered after that.)
4. **Add the SKUs** you're hunting and set your max price.
5. **Arm it.** 🦅 CardHawk watches; when stock flips, it moves.

> 📱 **Want to run it from your phone?** When the app starts it prints a `http://192.168.x.x:…` address — open that on any device on the same Wi-Fi for the full dashboard.

---

## 🔄 Updates

CardHawk checks this repo for new releases on its own.

- 🪟 **Windows** — fully **silent**. New versions download and install in the background; you're always current.
- 🍎 **macOS** — **assisted**. CardHawk tells you when an update is out and downloads the `.dmg`; you drag it to Applications to finish. (Apple requires a paid Developer ID for silent Mac updates — that's on the roadmap.)

You can also force a check any time from the app's tray/menu: **"Check for updates…"**

### 🪟 Do Windows users need a fresh install?

**Normally, no.** From **v0.11.3 onward** updates are clean, full-file downloads that apply automatically — just keep using the app (or hit **"Check for updates…"**).

**Do one fresh install if** you're coming from a very early build that wouldn't launch (e.g. an `Invalid file descriptor to ICU data` error, or a Start-menu shortcut pointing at a `Temp` folder). That was a bad-update bug, now fixed. To escape it cleanly: grab the latest **`CardHawk-Setup-x.y.z.exe`** and run it once. **Your watch list, settings, and templates are safe** — they live in your user profile, not the app folder, so a reinstall never wipes them.

---

## 📁 Where your stuff lives

Your data is stored in your **user profile**, *outside* the app — so updates and reinstalls never touch it.

| What | 🪟 Windows | 🍎 macOS |
|---|---|---|
| **Templates** (saved watch lists) | `%APPDATA%\cardhawk-desktop\templates` | `~/Library/Application Support/cardhawk-desktop/templates` |
| **Settings + watch list** (`config.json`) | `%APPDATA%\cardhawk-desktop\` | `~/Library/Application Support/cardhawk-desktop/` |
| **Logs** | `Documents\CardHawk\logs` | `~/Documents/CardHawk/logs` |

> 💡 **Easiest way there:** the app's **tray menu → "Open templates folder…"** (and **"View logs…"**) opens these for you — no need to paste a path.
>
> On Windows, paste `%APPDATA%\cardhawk-desktop` into the File Explorer address bar (that expands to `C:\Users\<you>\AppData\Roaming\cardhawk-desktop`). To share a watch list, copy a `.json` out of `templates\` — drop it into someone else's `templates\` folder and it shows up in their template picker.

---

## 🆘 Troubleshooting

<details>
<summary><b>🍎 macOS: "CardHawk can't be opened" on first launch (Gatekeeper)</b></summary>

<br/>

The app isn't notarized by Apple yet, so macOS double-checks the first launch. This is expected and safe to bypass for an app you downloaded yourself:

**Easiest:** **Right-click** (or Control-click) the app in Applications → **Open** → **Open** again in the dialog. macOS remembers your choice after that.

**Or** via System Settings → **Privacy & Security** → scroll down → **Open Anyway**.

**Or** from Terminal, clear the quarantine flag (replace the name if your app installed under a different label):
```bash
xattr -dr com.apple.quarantine "/Applications/CardHawk.app"
```
</details>

<details>
<summary><b>🪟 Windows: SmartScreen "Windows protected your PC"</b></summary>

<br/>

Because the installer isn't yet code-signed with an EV certificate, SmartScreen may warn on first run. Click **More info** → **Run anyway**. This goes away as the app builds reputation / once signing is added.
</details>

<details>
<summary><b>🔌 It opened Chrome but won't connect / "no session"</b></summary>

<br/>

Make sure you logged into the retailer **inside the Chrome window CardHawk opened** (not your everyday Chrome). That dedicated window is the session CardHawk drives. Close and reopen the app if needed — your login persists.
</details>

<details>
<summary><b>📱 The phone dashboard won't load</b></summary>

<br/>

Your phone and computer must be on the **same Wi-Fi network**. Use the `http://192.168.x.x:…` address the app prints on startup (not `localhost`). Some networks with "client isolation" / guest mode block device-to-device traffic — switch to your main network.
</details>

---

## 🛡️ Responsible use

CardHawk exists to give a **regular collector** a fair shot against scalper bots — and the design enforces that:

- ✅ It runs **only in your own logged-in session** — no multi-accounting, no proxy rotation.
- ✅ Purchases are **hard-capped at 2** per drop. There is no setting to raise it.
- ✅ It **does not** defeat CAPTCHAs, evade anti-bot systems, or flood retailers with traffic.
- ✅ Nothing is bought unless **you** arm it.

Use it to catch a couple of boxes for yourself. Respect each retailer's terms and your local laws. 🤝

---

<div align="center">

<sub>This repository hosts **installers and the update feed** for CardHawk. Source is maintained privately.</sub>

<br/>

**[⬇️ Get the latest release](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)** · Made for fans, not flippers. 🦅

</div>
