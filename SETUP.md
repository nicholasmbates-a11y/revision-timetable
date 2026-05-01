# Revision Timetable — Setup Guide

You have **four files** that work together:

1. **`index.html`** — a smart launcher that auto-detects whether the visitor is on a phone, tablet, or computer
2. **`revision-timetable.html`** — desktop / laptop optimised
3. **`revision-timetable-mobile.html`** — iOS / Android optimised
4. **`SETUP.md`** — this guide

## Running on a desktop / laptop

Just open `revision-timetable.html` (or `index.html`) directly in any modern browser.

## Running on iOS or Android

iOS Safari and Android Chrome **don't allow JavaScript to run from local HTML files** — they need to be hosted at a URL. You can't AirDrop or email the file and have it just work; you need to host it once and then the URL works on every device.

### Option 1: GitHub Pages (free, ~3 minutes, recommended)

1. Go to **github.com** and sign up if you don't have an account.
2. Click **+ → New repository**. Give it any name (e.g. `revision-timetable`). Public, with a README. **Create**.
3. **Add file → Upload files**. Drag in **all four files**. Commit.
4. **Settings → Pages** (sidebar). Source: **Deploy from a branch**, `main`, `/ (root)`. **Save**.
5. Wait ~1 minute. The Pages settings page will show your URL like `https://yourusername.github.io/revision-timetable/`.
6. Open that URL on any device. The launcher auto-detects and loads the right version.

**On iOS:** open the URL in Safari, tap the Share icon (⬆) → **Add to Home Screen** → Add. You get a full-screen app icon on your home screen.

**On Android:** open the URL in Chrome, tap the menu (⋮) → **Add to Home screen** or **Install app**.

### Option 2: Netlify Drop (drag-and-drop, no account needed)

Go to **app.netlify.com/drop**. Put all four files in a folder, drag the folder onto the page. Done.

### Option 3: Cloudflare Pages

**pages.cloudflare.com** — free permanent hosting. Same drag-and-drop idea.

## Updating the app on already-deployed phones

This is important because **browser caching** can cause phones to show an old version after you re-upload.

### How updates work now

The HTML files include cache-busting headers (`Cache-Control: no-cache`) telling browsers to always check for the latest version when online. The `index.html` launcher also appends a timestamp (`?v=...`) to the URL it redirects to, so even aggressive iOS Safari caching gets bypassed within ~5 minutes.

**Your update workflow:**

1. Delete the old HTML files in your GitHub repo
2. Upload the new ones
3. GitHub Pages serves the new version within ~1 minute
4. Phones that visit via `index.html` (the launcher) will pick up the change within ~5 minutes
5. Phones that bookmarked the inner URL directly may need to close and reopen Safari, or pull-to-refresh

**To force an instant update for a stuck phone:**

- Tell the user to fully close Safari (swipe up from home, swipe Safari away) and reopen
- Or: pull-to-refresh on the page (drag down from the top)
- Or: tap the URL bar, then tap Go again
- Or: in Safari Settings → Advanced → Website Data → find your site → Remove
- Or: if the app was added to home screen as a PWA on iOS, occasionally the only fix is to remove the icon from home screen and re-add it. This happens rarely — usually only after a long period of inactive use.

### Will updates lose user progress? No.

User data (subjects, sessions, badges, exam dates, past papers, weekly reviews, settings) lives in `localStorage`, which is **completely separate** from the cached HTML. Updating the HTML never touches `localStorage`.

The only things that wipe user data:
- Manually clearing site data via Safari Settings → Clear History and Website Data
- Deleting the home-screen icon on iOS in standalone PWA mode (because iOS sandboxes data per-PWA)
- Using Private Browsing mode (data is wiped when the tab closes)

For students worried about backup: the **⬇ Export** button downloads a JSON file containing everything, which can be re-imported via **⬆ Import**. Encourage them to do this once a month and save the file to iCloud Drive or email it to themselves.

## Forcing a specific version

Append `?force=desktop` or `?force=mobile` to your URL to override auto-detection:

- `https://your-url/?force=desktop` — always loads desktop version
- `https://your-url/?force=mobile` — always loads mobile version

## Tips for using on iOS

- **Don't use Private Browsing** — Safari wipes localStorage when you close a private tab.
- **Export regularly** with the ⬇ Export button as a backup. Save the JSON file to iCloud Drive.
- **Add to Home Screen** for the best experience — full-screen, dedicated icon, no browser bars.
- The same URL works on multiple devices, but the data lives separately on each. To move data, use Export on one device + Import on the other.

## Alternative: Documents by Readdle (no hosting)

If you don't want to host:

1. Install **Documents by Readdle** (free, App Store)
2. AirDrop or email the HTML files to your phone, save to a Documents folder
3. Tap `index.html` inside Documents — it opens with JavaScript working

Less convenient than hosting, but works without setting up GitHub.
