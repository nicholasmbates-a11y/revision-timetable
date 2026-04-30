# Revision Timetable — Setup Guide

You now have **three files** that work together:

1. **`index.html`** — a smart launcher that auto-detects whether the visitor is on a phone, tablet, or computer, and loads the right version
2. **`revision-timetable.html`** — desktop / laptop optimised
3. **`revision-timetable-mobile.html`** — iOS / Android optimised with bottom nav, FAB, swipe gestures, haptics, sounds, and PWA features

## Running on a desktop / laptop

Just open `revision-timetable.html` (or `index.html`) directly in any modern browser. JavaScript runs and your data saves automatically.

## Running on iOS or Android

iOS Safari (and Android Chrome) **don't allow JavaScript to run from local HTML files** — they need to be hosted at a URL. This means you can't AirDrop or email the file and have it just work; you need to host it once and then the URL works on every device.

### Option 1: GitHub Pages (free, ~3 minutes, recommended)

1. Go to **github.com** and create a free account if you don't have one.
2. Click **+ → New repository**. Give it any name (e.g. `revision-timetable`). Set it to Public. Tick "Add a README". Click **Create repository**.
3. Click **Add file → Upload files**. Drag in **all three files** (`index.html`, `revision-timetable.html`, `revision-timetable-mobile.html`). Commit them.
4. Go to **Settings → Pages** (left sidebar).
5. Under "Source", select **Deploy from a branch**, choose `main`, folder `/ (root)`. Click **Save**.
6. Wait ~1 minute. Refresh the Pages settings page — you'll see a URL like `https://yourusername.github.io/revision-timetable/`.
7. Open that URL on any device (iPhone, iPad, Android, Mac, PC). It auto-detects and loads the right version!

**To install it as an app on iOS:** open the URL in Safari, tap the Share icon (⬆) → **Add to Home Screen** → Add. You now have an icon on your home screen that opens full-screen with no browser chrome.

**On Android:** open the URL in Chrome, tap the menu (⋮) → **Add to Home screen** or **Install app**.

### Option 2: Netlify Drop (drag-and-drop, no account needed)

1. On a computer, go to **app.netlify.com/drop**.
2. Create a folder containing all three HTML files, then drag the **folder** onto the Netlify page.
3. Netlify gives you a URL instantly (e.g. `random-name-123.netlify.app`).
4. Open that URL on any device — done.

(Without an account the URL is temporary. Sign up free to keep it permanent.)

### Option 3: Cloudflare Pages

Drag-and-drop deploy at **pages.cloudflare.com**. Free permanent hosting. Same idea — upload all three files together.

## How auto-detection works

When someone visits `index.html`:

- **iPhone, iPad, Android phone** → loads the mobile version (with bottom nav, swipe gestures, haptics)
- **Mac, PC, big tablet** → loads the desktop version (with the full top menu bar and wide calendar)
- **Edge case** (touch laptop, big iPad) → falls back to mobile if there's a touch screen *and* the smaller screen dimension is ≤ 820px

There's a 200ms loading screen showing the gradient logo before the redirect fires, with manual override links that appear if anything goes wrong.

## Forcing a specific version

You can append `?force=desktop` or `?force=mobile` to the URL to override the detection:

- `https://your-url/?force=desktop` — always loads desktop version
- `https://your-url/?force=mobile` — always loads mobile version

Useful if you want to use the mobile version on a small laptop window, or test the desktop UI from your phone.

## Tips for using on iOS

- **Don't use Private Browsing** — Safari wipes localStorage when you close a private tab, so all your revision data would be lost.
- **Export regularly** with the ⬇ Export button as a backup. The JSON file can be saved to iCloud Drive.
- **Add to Home Screen** for the best experience — full-screen, dedicated icon, no browser bars eating your screen.
- The same data works on both versions if you have it on the same device (they share localStorage). Use Export + Import to move data between devices.

## Alternative: Documents by Readdle (no hosting needed)

If you really want to run the files locally on iOS without hosting:

1. Install **Documents by Readdle** (free) from the App Store.
2. AirDrop or email the HTML files to your phone, save them into a folder in Documents.
3. Tap `index.html` inside Documents — it opens in their built-in browser with JavaScript working, and the launcher will redirect you to the mobile version.

This works but is less convenient than just hosting the files.
