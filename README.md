# Sari-Sari Store — Offline-Ready Website / PWA

This project is a small sari-sari store inventory and sales tracker that can be published as a website and installed on a phone as a Progressive Web App (PWA).

## Project files

```text
sari-sari-pwa/
├── index.html          # Store application (HTML, CSS, and JavaScript)
├── manifest.json       # App name, display settings, and icons
├── sw.js               # Service worker for offline caching
├── README.md           # Project instructions
└── icons/
    ├── icon-192.png    # App icon
    └── icon-512.png    # App icon
```

## Run locally

1. Keep all files and the `icons` folder together.
2. Open the project folder in VS Code or GitHub Codespaces.
3. Start a local web server. For example, in the terminal run:

   ```bash
   python3 -m http.server 8000 --bind 0.0.0.0
   ```

4. Open port `8000` using the **Ports** panel in Codespaces, or open the local server address in your browser.
5. Open the app while connected to the internet and let it finish loading. The service worker will cache the app files.
6. Reload the page once, then test offline by disconnecting from the internet and reopening the app.

> Service workers require HTTPS or localhost. Opening `index.html` directly as a `file://` URL will not enable offline caching.

## Publish with GitHub Pages

1. Create or open the GitHub repository for this project.
2. Upload the contents of this project folder to the repository. Keep `index.html`, `manifest.json`, and `sw.js` in the publishing folder's top level. Do not put them one folder deeper unless you configure GitHub Pages to publish from that subfolder.
3. Open the repository's **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and the `/(root)` folder, then click **Save**.
6. Wait for the GitHub Pages deployment to finish. Use the **Visit site** link shown in the Pages settings. The address will look like:

   ```text
   https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/
   ```

7. Open that HTTPS address on your phone while connected to the internet. Let it load, then use the browser menu to **Install app** or **Add to Home Screen**.
8. Open the installed app once while online. Then test offline by disconnecting from the internet and reopening it.

## Image uploads

- Tap the store name in the app header to edit the store name and upload or remove the store logo.
- Open **Stock**, then choose **Add product** or **Edit** on an existing product to upload or remove its product image.
- Images are resized in the browser and saved with the app's existing `localStorage` data on that device and browser.
- Keep photos reasonably sized and avoid adding too many images because browser storage is limited. If storage fills up, the app will show a warning.
- The installed app icon on the phone's home screen is separate from the in-app store logo. To change the home-screen icon, replace `icons/icon-192.png` and `icons/icon-512.png`, then publish the update.

## Offline behavior

- The first visit must be online so the browser can download and cache the app files.
- After the app has been cached successfully, its interface and `localStorage`-based features can work offline on the same device and browser.
- When publishing an update, change the cache name in `sw.js` (for example, from `sari-sari-store-v2` to `sari-sari-store-v3`) so devices fetch the updated app files.

## Data and privacy notes

- This app currently saves products, stock changes, and utang records in the browser's `localStorage`.
- Data stays on that browser, device, and website address. It is not uploaded to a shared database and does not automatically sync between phones or computers.
- A published site is publicly reachable. Anyone can open the site, but each visitor gets their own browser-local data. Avoid entering private customer information on a public or shared device.
- Changing from a local development address to the published HTTPS address creates a different browser storage origin. Existing local data will not automatically move to the published website. Make a backup before switching; this version does not include an export/import backup feature.
- Clearing the browser's website data may delete local records. Shared multi-device records and safer backups require a separate database and sign-in system.

## Installing the app

- **Android:** Open the published HTTPS site in Chrome, open the browser menu, then choose **Install app** (or **Add to Home Screen**, depending on the browser).
- **iPhone:** Open the published HTTPS site in Safari, tap **Share**, choose **Add to Home Screen**, and enable **Open as Web App** when that option appears.



## Mobile layout

- On phones and small screens (up to 767px wide), the bottom navigation is replaced by a hamburger menu in the header.
- Tap the hamburger button to open Sell, Stock, and Utang. Tap an item to switch pages; tap outside the menu to close it.
- On wider screens, the regular navigation is shown.
