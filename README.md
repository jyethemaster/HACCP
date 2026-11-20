# HACCP Billy's Coffee – Android app

This project wraps the HACCP registration page (`www/index.html`) as an Android app.
GitHub builds the app file (APK) for you – you do not need to install anything on a computer.

## One-time setup
1. Create a **private** repository on github.com (private, because `debug.keystore` is the app's signing key).
2. Upload everything from this folder to the repository (keep the `.github` folder; on github.com use "Add file → Upload files" and drag in the unzipped folder contents). The default branch must be called `main`.
3. Open the **Actions** tab. The "Build Android APK" workflow starts automatically (or choose it and click "Run workflow").
4. When it finishes (about 5 minutes, green tick), open the run and download the **haccp-apk** artifact at the bottom. Unzip it: inside is `app-debug.apk`.
5. Put `app-debug.apk` on the tablet (e.g. via Google Drive or USB) and open it. Android asks to allow installing from this source – allow it for that app only (Chrome or Files). Install.

## Updating the app
Replace `www/index.html` in the repository with the new version and commit. The workflow builds a new APK. Install it over the old app: the data stays, because every build uses the same signing key (`debug.keystore`). **Do not uninstall the app first – that deletes the records.**

## Where is the data?
- Records live inside the app (private to the app). Uninstalling the app or clearing its data deletes them.
- Once a week, on the first save, the app writes a backup file to **Documents/HACCP** on the tablet. These files survive uninstalling. Copy them off the tablet regularly (Google Drive, e-mail, USB).
- "Back-up maken", the Excel file and "Overzicht opslaan" also save into Documents/HACCP. If the tablet refuses that folder, Android's share sheet opens instead – pick Drive, e-mail, etc.
- To restore: Overzicht → "Back-up terugzetten" and pick the `.json` file.

## Printing
Android apps of this type cannot print directly. "Overzicht opslaan" creates `haccp-overzicht-DATUM.html` in Documents/HACCP. Open it in Chrome (Files app → tap the file → Chrome) and choose Print or Save as PDF.

## Not tested
This was prepared without a real device or a real build run. If the workflow fails, open the failed step in the Actions tab and send the error text to get it fixed.
