# Operations — install on your phone

Your study system is now a full **Progressive Web App (PWA)**: it installs to your
home screen, opens full-screen with no browser bars, works offline, and keeps your
progress, streaks and day counter on the device.

There are two ways to get it onto your phone. **Option A is the real app experience.**

---

## Option A — Host it (proper app, offline + installable) ✅ recommended

A PWA has to be served over the web (https), not opened as a file. Easiest free route:

### GitHub Pages (free, ~3 min)
1. Go to github.com → **New repository** → name it e.g. `ops` → Public → Create.
2. Click **Add file → Upload files**, drag in **all files from this folder**
   (`index.html`, `manifest.webmanifest`, `sw.js`, and all the `icon-*.png` /
   `apple-touch-icon.png`). Commit.
3. Repo **Settings → Pages** → Source: `main` branch, `/root` → Save.
4. After a minute you get a URL like `https://yourname.github.io/ops/`.
5. Open that URL **on your phone**, then:
   - **iPhone (Safari):** Share button → **Add to Home Screen**.
   - **Android (Chrome):** menu **⋮** → **Install app** / **Add to Home screen**.

That's it — tap the icon and it runs like a native app, even in airplane mode.

> Any static host works the same way: Netlify Drop (netlify.com/drop — just drag the
> folder), Cloudflare Pages, Vercel, etc. Just keep all files together in one folder.

---

## Option B — Just open the file (no hosting)

You can also open `index.html` directly on your phone (e.g. save it to Files and tap it).
It still works and looks identical — **but** because a local file can't run a service
worker, the browser may not offer "Add to Home Screen" as a true app, and on some
browsers local storage is cleared more aggressively.

**Important for Option B:** open the actual saved file directly. If you view it inside a
preview/sandbox that blocks storage, the day counter restarts each time. Use the
**Export** button (Data tab) regularly to back up, and **Import** to restore.

---

## Your data
- Everything is stored **locally on your device** — nothing is uploaded anywhere.
- The **day counter** starts from the first time you open the app and keeps counting
  offline; closing the app doesn't reset it.
- Use **Data → Export** to save a `.json` backup (e.g. before switching phones), and
  **Import** to bring it back. Importing keeps the earlier of the two start dates.

## Updating the app later
If you host it (Option A) and later change a file, edit `sw.js` and bump
`const CACHE = "ops-v1";` to `"ops-v2";` so phones pick up the new version.
