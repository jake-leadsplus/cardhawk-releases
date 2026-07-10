# CardHawk

**A personal-use restock watcher and checkout assistant for Pokémon TCG drops on Target.**

CardHawk watches a product's availability and, when you ask it to, walks your own
logged-in browser through checkout. It runs in *your* Chrome session — no proxies,
no throwaway accounts, no CAPTCHA solving. This repository hosts the installers and
the auto-update feed; the source is maintained privately.

[**Download the latest release →**](https://github.com/jake-leadsplus/cardhawk-releases/releases/latest)

| Platform | Download | Install |
|---|---|---|
| Windows 10/11 | `CardHawk-Setup-<version>.exe` | Run the installer. Updates apply themselves silently in the background. |
| macOS (Apple Silicon) | `CardHawk-<version>-arm64.dmg` | Open the `.dmg`, drag CardHawk to **Applications**. On first launch use **right-click → Open** (see [the Gatekeeper note](#macos-first-launch-gatekeeper)). |

On Windows, take the `.exe`. On an Apple-Silicon Mac (M1–M4), take the `-arm64.dmg`.

---

## What it does

A drop can sell out in the time it takes to refresh the page. CardHawk narrows that
gap for a regular buyer without behaving like a bot:

- **Watch** — a read-only monitor polls the retailer's availability API and detects
  the `OUT_OF_STOCK → IN_STOCK` change, rather than waiting on a "notify me" email.
  It polls through your real browser session, so there is no separate footprint.
- **Buy** — when you've armed it, CardHawk drives checkout in your own logged-in tab:
  add to cart, load checkout, and place the order (entering your CVV if the card
  prompts for it). Nothing is purchased unless you turn buying on yourself.

The tool does not open a throwaway browser, rotate proxies or identities, defeat
CAPTCHAs, or flood the retailer. Both halves run inside your real, signed-in Chrome.

## How buying is gated

Every session starts in a safe state and stays there until you change it. Buying has
three levels, chosen in the dashboard:

- **Notify** — the default. On a restock it alarms and opens the tab; it never buys.
- **Prep** — on a restock it adds to cart and loads checkout to the "ready to place"
  point, then stops and waits for you to confirm.
- **ACO (Auto Checkout)** — hands-off. It carts, checks out, and places the order on
  its own.

Two independent switches guard an automatic purchase: a per-session safety latch
(always off at launch, never remembered between runs) and the Auto Checkout toggle.
Loading a watch list never changes either one.

## Features

- **Fast restock detection** on a warm, real browser session.
- **Runs in your own Chrome** — your login, your card, your IP. No proxies or
  throwaway browsers.
- **Hard 2-item cap.** Quantity is clamped to at most 2 per order on every path.
  There is no setting to raise it.
- **Spend and item guards.** An unreadable order total, an over-cap item count, a
  pickup item, or a cart that doesn't hold exactly your item all cause CardHawk to
  refuse to place rather than guess.
- **Live dashboard, on your desktop or phone.** A built-in dashboard mirrors status,
  price, and per-SKU settings, and streams updates live. Open it from the app window
  or from any device on the same Wi-Fi. It's protected by a per-run token, and the
  CVV field only accepts input on the host machine.
- **Watch lists (templates).** Track many Target SKUs at once, each with its own
  price cap. Save and share lists as files.
- **First-run setup.** A short guided setup walks you through signing in and picking a
  starting list, and installs Google Chrome for you if it isn't already present.
- **Auto-updates.** Windows updates silently; macOS offers a one-tap assisted update.
  Your watch lists, settings, and templates are never touched by an update.

> Support for retailers beyond Target is in development and not yet enabled in the app.

---

## Quick start

1. **Install** from the table above and open CardHawk.
2. On first run it opens a dedicated Chrome window and walks you through setup.
3. **Sign in** to `target.com` in that window and save your card. This is a one-time
   step — the session is remembered afterward.
4. **Add the SKUs** you're watching and set a max price for each.
5. Choose your level (**Notify**, **Prep**, or **ACO**) when you're ready. CardHawk
   watches; when stock changes, it acts according to the level you set.

To control it from your phone, open the `http://192.168.x.x:…` address the app shows
on startup from any device on the same Wi-Fi.

## Updates

CardHawk checks this repository for new releases on its own.

- **Windows** — fully silent. New versions download and install in the background.
- **macOS** — assisted. CardHawk tells you when an update is available and downloads
  the `.dmg`; you drag it to Applications to finish. (Silent updates on macOS require
  a paid Apple Developer ID, which is on the roadmap.)

You can force a check any time from the tray/menu: **"Check for updates…"**

**Do Windows users ever need a fresh install?** Normally no — updates are clean,
full-file downloads that apply automatically. Do one manual reinstall only if you're
coming from a very early build that wouldn't launch (for example an
`Invalid file descriptor to ICU data` error, or a Start-menu shortcut pointing at a
`Temp` folder); that was a bad-update bug and is now fixed. Grab the latest
`CardHawk-Setup-<version>.exe` and run it once. Your watch lists, settings, and
templates are safe — they live in your user profile, not the app folder.

## Where your data lives

Your data is stored in your user profile, outside the app, so updates and reinstalls
never touch it.

| What | Windows | macOS |
|---|---|---|
| Templates (saved watch lists) | `%APPDATA%\cardhawk-desktop\templates` | `~/Library/Application Support/cardhawk-desktop/templates` |
| Settings + watch list (`config.json`) | `%APPDATA%\cardhawk-desktop\` | `~/Library/Application Support/cardhawk-desktop/` |
| Logs | `Documents\CardHawk\logs` | `~/Documents/CardHawk/logs` |

The tray menu's **"Open templates folder…"** and **"View logs…"** open these for you.
To share a watch list, copy a `.json` out of the `templates` folder into someone
else's — it shows up in their template picker.

---

## Troubleshooting

<a id="macos-first-launch-gatekeeper"></a>
<details>
<summary><b>macOS: "CardHawk can't be opened" on first launch (Gatekeeper)</b></summary>

<br/>

The app isn't notarized by Apple yet, so macOS double-checks the first launch. This
is expected for an app you downloaded yourself:

- **Right-click** (or Control-click) CardHawk in Applications → **Open** → **Open**
  again in the dialog. macOS remembers your choice after that.
- Or: System Settings → **Privacy & Security** → **Open Anyway**.
- Or, from Terminal, clear the quarantine flag:
  ```bash
  xattr -dr com.apple.quarantine "/Applications/CardHawk.app"
  ```
</details>

<details>
<summary><b>Windows: SmartScreen "Windows protected your PC"</b></summary>

<br/>

The installer isn't code-signed with an EV certificate yet, so SmartScreen may warn
on first run. Click **More info → Run anyway**. This goes away as the app builds
reputation, or once signing is added.
</details>

<details>
<summary><b>It opened Chrome but won't connect / "no session"</b></summary>

<br/>

Make sure you signed in to the retailer **inside the Chrome window CardHawk opened**
(not your everyday Chrome). That dedicated window is the session CardHawk drives.
Close and reopen the app if needed — your login persists.
</details>

<details>
<summary><b>The phone dashboard won't load</b></summary>

<br/>

Your phone and computer must be on the same Wi-Fi network. Use the
`http://192.168.x.x:…` address the app prints on startup (not `localhost`). Some
networks with "client isolation" or guest mode block device-to-device traffic —
switch to your main network.
</details>

---

## Responsible use

CardHawk is meant to give a regular collector a fair shot, and the design reflects
that:

- It runs only in your own logged-in session — no multi-accounting, no proxy rotation.
- Purchases are capped at 2 per order, with no setting to raise it.
- It does not defeat CAPTCHAs, evade anti-bot systems, or flood retailers with traffic.
- Nothing is bought unless you turn buying on.

Use it to pick up a couple of items for yourself, and respect each retailer's terms
of service and your local laws.

---

<sub>This repository hosts the installers and the auto-update feed for CardHawk. The
source is maintained privately.</sub>
