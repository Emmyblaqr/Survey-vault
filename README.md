# Field Vault — Survey Records

A private, browser-based tool for filing survey screenshots. Upload screenshots per survey, split them by "character" (a persona/attempt identity), search any word across all your screenshots, and auto-extract fields like name, surname, date of birth, email, phone, state, and age from the text in the images.

Everything runs entirely in your browser — there is no server and no account. Your screenshots and data are stored on your device only.

## Deploy on GitHub Pages (free)

1. Create a new GitHub repository (public or private both work; Pages on a private repo needs GitHub Pro/Team/Enterprise, so public is simplest).
2. Upload **`index.html`** to the root of the repo. That's the only file required.
3. Go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to `Deploy from a branch`.
5. Set **Branch** to `main` (or whichever branch has the file) and folder to `/ (root)`, then **Save**.
6. GitHub gives you a URL like `https://yourusername.github.io/your-repo-name/` within a minute or two. Open it on your phone and add it to your home screen for an app-like feel.

## Important: your data lives in the browser, not the cloud

This app stores everything locally (IndexedDB) in whichever browser and device you're using it on. That means:

- Data does **not** sync between your phone and laptop, or between Safari and Chrome on the same phone.
- Clearing your browser's site data/cache will erase it.
- If you switch phones, the data doesn't come with you automatically.

**Use the Export Backup / Import Backup buttons on the home screen** to protect against this — Export downloads a single `.json` file with everything (including the images), and Import restores from that file on any device/browser. Get in the habit of exporting a backup after finishing a batch of surveys, and keep the file somewhere safe (cloud drive, email to yourself, etc.).

## What's inside `index.html`

Just one self-contained file — no build step, no dependencies to install. It loads Tesseract.js (for on-device text recognition) from a CDN at runtime, so the device needs an internet connection the first time it scans a screenshot (the OCR language data gets cached after that).

## Notes

- OCR (text scanning) runs on-device and takes a few seconds per screenshot.
- Very large screenshots may occasionally fail to save if the device is low on storage — a smaller/compressed screenshot usually fixes it.
- Auto-extracted fields (name, DOB, email, etc.) are a best guess from the scanned text — always double-check them, since OCR isn't perfect. You can edit any field by hand on the character's ID card.
