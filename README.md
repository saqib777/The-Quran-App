# Noor — My Qur'an App (Electron Desktop Build)

A personal offline Islamic reference app: full Qur'an (Arabic + English + Urdu),
six major Hadith collections + 40 Hadith Nawawi, Obligations, People of Islam,
Dua, and an Islamic (Hijri) Calendar — all bundled to work fully offline.
Only the per-ayah Tafsir commentary needs an internet connection.

## Project layout

```
noor-electron/
├── main.js            Electron main process (creates the window)
├── package.json        App metadata + electron-builder packaging config
├── build/
│   └── icon.png         App icon
└── app/
    └── index.html        The entire app (UI + bundled Qur'an/Hadith data)
```

## Run it in development

```bash
npm install
npm start
```

This opens the app in a proper desktop window (title bar, taskbar icon, no browser
chrome, works fully offline for Qur'an & Hadith).

## Build an installable app

Run this **on the OS you want to build for** — building for Windows needs to
happen on Windows (or a Mac/Linux machine with Wine installed).

```bash
npm install
npm run dist         # builds for your current OS
npm run dist:win     # Windows: creates an NSIS installer + a portable .exe
npm run dist:mac     # macOS: creates a .dmg
npm run dist:linux   # Linux: creates an AppImage
```

Output lands in the `release/` folder:
- **Windows**: `Noor Setup 1.0.0.exe` (installer, adds Start Menu + Desktop shortcut) and `Noor 1.0.0.exe` (portable, no install needed)
- **macOS**: `Noor-1.0.0.dmg`
- **Linux**: `Noor-1.0.0.AppImage`

## Updating the app later

If you ask Claude for changes to the app, you'll just get an updated
`app/index.html` — drop it into `app/` (replacing the old one) and re-run
`npm run dist:win`. `main.js` and `package.json` won't need to change unless
you want to rename the app or change the icon.

## Notes

- The window is 1360×860 by default (resizable, min 900×600).
- Google Fonts (Amiri, Lora, Noto Nastaliq Urdu) load from the internet on
  first run for nicer typography; if offline, the app falls back to system fonts.
- Tafsir (per-ayah commentary) is fetched live from GitHub when you tap
  "Meaning & Context" — this is the one feature that needs internet.
"# The-Quran-App" 
