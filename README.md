<div align="center">

# 🦅 CardHawk

**Restock watcher & one‑tap checkout for Pokémon TCG drops on Target.**

Runs inside *your own* logged‑in Chrome — no proxies, no throwaway accounts, no CAPTCHA solving.

<br/>

[![Latest release](https://img.shields.io/github/v/release/jake-leadsplus/cardhawk-releases?style=for-the-badge&label=Latest&labelColor=11131a&color=7c3aed)](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)
&nbsp;
[![Windows](https://img.shields.io/badge/Windows-10%20%2F%2011-0078D6?style=for-the-badge&labelColor=11131a&logo=windows11&logoColor=white)](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)
&nbsp;
[![macOS](https://img.shields.io/badge/macOS-Apple%20Silicon-000000?style=for-the-badge&labelColor=11131a&logo=apple&logoColor=white)](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)

<br/>

### ⬇&nbsp;&nbsp;[Download the latest release](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)

<sub>Windows 10/11 · macOS (Apple Silicon) · updates itself</sub>

</div>

<br/>

> **What it is** — A drop can sell out in the time it takes to refresh the page.
> CardHawk narrows that gap for a regular buyer without behaving like a bot: it
> watches a product's availability and, when you tell it to, walks your own
> signed‑in browser through checkout. This repository hosts the installers and the
> auto‑update feed; the source is maintained privately.

<br/>

**Jump to:**
[Download](#-download) · [How it works](#-how-it-works) · [Buying modes](#-buying-modes) · [Features](#-features) · [Quick start](#-quick-start) · [Updates](#-updates) · [Your data](#-where-your-data-lives) · [Troubleshooting](#-troubleshooting) · [Responsible use](#-responsible-use)

---

## 📥 Download

| Platform | File | Install |
| :------- | :--- | :------ |
| **Windows 10/11** | `CardHawk-Setup-<version>.exe` | Run the installer — that's it. Updates apply themselves silently in the background. |
| **macOS (Apple Silicon)** | `CardHawk-<version>-arm64.dmg` | Open the `.dmg`, drag **CardHawk** to **Applications**. On first launch, **right‑click → Open** ([why?](#macos-first-launch-gatekeeper)). |

<div align="center"><sub>On Windows take the <code>.exe</code>. On an Apple‑Silicon Mac (M1–M4) take the <code>-arm64.dmg</code>.</sub></div>

---

## ⚙️ How it works

CardHawk has two halves, and both run inside your real, signed‑in Chrome — so there's
no separate footprint to flag.

<table>
<tr>
<td width="50%" valign="top">

### 👀 Watch

A read‑only monitor polls the retailer's availability API and catches the
`OUT_OF_STOCK → IN_STOCK` change — instead of waiting on a "notify me" email.

It polls *through your real browser session*, so it looks like ordinary browsing.

</td>
<td width="50%" valign="top">

### 🛒 Buy

When you've armed it, CardHawk drives checkout in your own logged‑in tab: add to
cart → load checkout → **place the order** (entering your CVV if the card asks).

The **only** click that ever commits money is *Place your order* — everything else
just advances a step or dismisses a popup.

</td>
</tr>
</table>

> It does **not** open a throwaway browser, rotate proxies or identities, defeat
> CAPTCHAs, or flood the retailer.

---

## 🔒 Buying modes

Every session starts **safe** and stays there until you change it. You pick the level in the dashboard:

| Mode | On a restock it… | Buys? |
| :--- | :--- | :--: |
| **Notify** *(default)* | Alarms and opens the product tab | ❌ Never |
| **Prep** | Adds to cart and loads checkout to *ready to place* | ⏸️ Only after you confirm |
| **ACO** *(Auto Checkout)* | Carts, checks out, and places the order — hands‑off | ✅ Yes |

Two independent switches guard an automatic purchase: a **per‑session safety latch**
(always off at launch, never remembered between runs) and the **Auto Checkout** toggle.
Loading a watch list never flips either one.

---

## ✨ Features

- 🦅 **Fast restock detection** on a warm, real browser session.
- 🔒 **Runs in your own Chrome** — your login, your card, your IP. No proxies, no throwaway browsers.
- 🧢 **Hard 2‑item cap.** Quantity is clamped to at most **2 per order** on every path. There is no setting to raise it.
- 🛡️ **Fail‑safe guards.** An unreadable total, an over‑cap item count, a pickup item, or a cart that doesn't hold *exactly* your item all make it **refuse to place** rather than guess.
- 📱 **Live dashboard, on desktop or phone.** Mirrors status, price, and per‑SKU settings and streams updates live. Open it from the app window or any device on the same Wi‑Fi — protected by a per‑run token, with CVV entry accepted only on the host machine.
- 🎯 **Watch lists (templates).** Track many Target SKUs at once, each with its own price cap. Save and share lists as files.
- 🚀 **First‑run setup.** A short guided flow handles sign‑in and a starting list — and installs Google Chrome for you if it isn't already present.
- 🔁 **Auto‑updates.** Windows updates silently; macOS offers a one‑tap assisted update. Your watch lists, settings, and templates are never touched by an update.

<div align="center"><sub>Currently focused on <b>Target</b>. Support for more retailers is in development and not yet enabled in the app.</sub></div>

---

## 🚀 Quick start

1. **Install** from the [download table](#-download) above and open CardHawk.
2. On first run it opens a dedicated Chrome window and walks you through setup.
3. **Sign in** to `target.com` in that window and save your card — a one‑time step; the session is remembered afterward.
4. **Add the SKUs** you're watching and set a max price for each.
5. Choose your level — **Notify**, **Prep**, or **ACO** — when you're ready.

> 📱 **Run it from your phone:** open the `http://192.168.x.x:…` address the app shows on startup from any device on the same Wi‑Fi.

---

## 🔄 Updates

CardHawk checks this repository for new releases on its own.

- **🪟 Windows** — fully **silent**. New versions download and install in the background.
- **🍎 macOS** — **assisted**. It tells you when an update is out and downloads the `.dmg`; you drag it to Applications to finish. *(Silent macOS updates need a paid Apple Developer ID — on the roadmap.)*

You can force a check any time from the tray menu → **"Check for updates…"**

<details>
<summary><b>Do Windows users ever need a fresh install?</b></summary>

<br/>

Normally **no** — updates are clean, full‑file downloads that apply automatically.
Do one manual reinstall only if you're coming from a very early build that wouldn't
launch (e.g. an `Invalid file descriptor to ICU data` error, or a Start‑menu shortcut
pointing at a `Temp` folder) — that was a bad‑update bug and is now fixed. Grab the
latest `CardHawk-Setup-<version>.exe` and run it once. **Your watch lists, settings,
and templates are safe** — they live in your user profile, not the app folder.
</details>

---

## 📁 Where your data lives

Your data is stored in your **user profile**, outside the app, so updates and reinstalls never touch it.

| What | 🪟 Windows | 🍎 macOS |
| :--- | :--- | :--- |
| **Templates** (saved watch lists) | `%APPDATA%\cardhawk-desktop\templates` | `~/Library/Application Support/cardhawk-desktop/templates` |
| **Settings + watch list** (`config.json`) | `%APPDATA%\cardhawk-desktop\` | `~/Library/Application Support/cardhawk-desktop/` |
| **Logs** | `Documents\CardHawk\logs` | `~/Documents/CardHawk/logs` |

> 💡 The tray menu's **"Open templates folder…"** and **"View logs…"** open these for you. To share a watch list, copy a `.json` out of `templates` into someone else's — it appears in their template picker.

---

## 🆘 Troubleshooting

<a id="macos-first-launch-gatekeeper"></a>
<details>
<summary><b>🍎 macOS: "CardHawk can't be opened" on first launch (Gatekeeper)</b></summary>

<br/>

The app isn't notarized by Apple yet, so macOS double‑checks the first launch. This is expected for an app you downloaded yourself:

- **Right‑click** (or Control‑click) CardHawk in Applications → **Open** → **Open** again. macOS remembers your choice after that.
- Or: System Settings → **Privacy & Security** → **Open Anyway**.
- Or, from Terminal, clear the quarantine flag:
  ```bash
  xattr -dr com.apple.quarantine "/Applications/CardHawk.app"
  ```
</details>

<details>
<summary><b>🪟 Windows: SmartScreen "Windows protected your PC"</b></summary>

<br/>

The installer isn't code‑signed with an EV certificate yet, so SmartScreen may warn on first run. Click **More info → Run anyway**. This clears up as the app builds reputation, or once signing is added.
</details>

<details>
<summary><b>🔌 It opened Chrome but won't connect / "no session"</b></summary>

<br/>

Make sure you signed in to the retailer **inside the Chrome window CardHawk opened** (not your everyday Chrome). That dedicated window is the session CardHawk drives. Close and reopen the app if needed — your login persists.
</details>

<details>
<summary><b>📱 The phone dashboard won't load</b></summary>

<br/>

Your phone and computer must be on the **same Wi‑Fi network**. Use the `http://192.168.x.x:…` address the app prints on startup (not `localhost`). Some networks with "client isolation" or guest mode block device‑to‑device traffic — switch to your main network.
</details>

---

## 🛡️ Responsible use

CardHawk is meant to give a regular collector a fair shot, and the design reflects that:

- ✅ It runs **only in your own logged‑in session** — no multi‑accounting, no proxy rotation.
- ✅ Purchases are **capped at 2 per order**, with no setting to raise it.
- ✅ It **does not** defeat CAPTCHAs, evade anti‑bot systems, or flood retailers with traffic.
- ✅ **Nothing** is bought unless you turn buying on.

Use it to pick up a couple of items for yourself, and respect each retailer's terms of service and your local laws.

---

<div align="center">

**[⬇ Get the latest release](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)**

<sub>This repository hosts the installers and the auto‑update feed for CardHawk. The source is maintained privately.</sub>

</div>
