SARI-SARI STORE — OFFLINE-READY WEBSITE / PWA

FILES
- index.html       The store app
- manifest.json    App name, display settings, and icons
- sw.js            Caches the app files so the app can open offline
- icons/           App icons (192px and 512px)

RUN LOCALLY
1. Keep all files and the icons folder together.
2. Open the folder in VS Code.
3. Start a local web server (for example, VS Code Live Server) and open index.html through that server.
   Service workers do not work when the page is opened directly as a file:// URL.
4. While online, open the app once and let it finish loading. The service worker will cache the app shell.
5. Reload once, then test by turning off Wi-Fi/mobile data and reopening the app.

PUBLISH WITH GITHUB PAGES
1. Sign in to GitHub and create a repository for the website.
2. Upload index.html, manifest.json, sw.js, the icons folder, and this README.txt.
   Keep index.html at the top level of the repository. Do not upload only the HTML file by itself.
3. Open the repository's Settings, then Pages.
4. Under the build/deployment source, choose Deploy from a branch.
5. Choose the main branch and the /(root) folder, then Save.
6. After GitHub Pages finishes publishing, use the Visit site link. The address will look like:
   https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/
7. Open that HTTPS address on the phone while connected to the internet, let it load, then add it to the Home Screen / install it from the browser menu.
8. Open the installed app once while online. Then test offline by disconnecting from the internet and reopening it.

IMPORTANT DATA NOTES
- This app currently saves products, sales-related stock changes, and utang records in localStorage in the browser.
- That data stays on that browser/device and website address. It is not uploaded to a shared database and does not automatically sync between phones or computers.
- A published site is publicly reachable. Anyone can open the site, but each visitor gets their own browser-local data. Do not put private customer information in a public shared device.
- Changing from your old local development address to the published HTTPS address creates a different browser storage origin. Existing local data will not automatically move to the published website. Make a backup before switching; this version does not yet include an export/import backup feature.
- If the browser's website data is cleared, local records may be deleted. A separate database and sign-in system would be needed for shared multi-device records and safer backups.

OFFLINE NOTES
- The first visit must be online so the browser can download and cache the app files.
- The app's interface and localStorage-based features can then work offline on the same device/browser, provided the site was cached successfully.
- When you publish an update, the service worker cache name should be changed in sw.js (for example, sari-sari-store-v2) so devices fetch the new app files.
