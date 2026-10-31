# Morrow Browser

A desktop web browser built with Electron, React, TypeScript and Vite. Morrow uses isolated Electron `WebContentsView` instances for tabs; browser pages have no Node integration and cannot access the React application's preload bridge.

## Run locally

```sh
npm install
npm run dev
```

Build the renderer and Electron main/preload bundles with `npm run build`, then launch with `npm start`.

## Shortcuts

- `⌘/Ctrl + T`: new tab
- `⌘/Ctrl + W`: close tab
- `⌘/Ctrl + L`: focus the address bar
- `⌘/Ctrl + R`: reload current page

Bookmarks and visit history are stored in local browser storage.

## Design system

Morrow uses a soft, low-contrast palette, a spacious new-tab page, and a guided first-run setup. **DM Sans** handles interface text, **Manrope** display headings, and **Georgia** the italic accent.

| Palette | Background | Surface | Soft surface | Border | Text | Muted text | Accent | Accent tint |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Light | `#f8f7f5` | `#ffffff` | `#f5f3f0` | `#eae8e4` | `#272623` | `#9c9993` | `#aa786c` | `#f1e8e3` |
| Dark | `#1c1d1c` | `#252625` | `#2b2c2b` | `#383936` | `#eeece8` | `#a19f99` | `#dfa394` | `#382c29` |

Warm rose and clay tones provide restrained accents across the new-tab page, onboarding, and browser chrome. Shadows use translucent warm charcoal/brown. Shortcut tiles can also use per-shortcut colors.

## Build installers

Morrow uses electron-builder for desktop installers. On macOS, run:

```sh
npm install
npm run package:mac
```

The branded DMG is written to `release/` as `Morrow-<version>-<architecture>.dmg` and includes the Morrow app icon, a custom install background, and an Applications shortcut. `npm run package:mac:all` also creates a ZIP. Windows builds use `npm run package:win` (NSIS installer), and Linux builds use `npm run package:linux` (AppImage and deb). Run each platform's build on that operating system.

The macOS package is unsigned unless a Developer ID certificate is configured. Gatekeeper may show an unidentified-developer warning until the app is signed and notarized for distribution.

## Importing from another browser

The first-run setup can import bookmarks from Netscape-format HTML or browser JSON (including Chrome/Edge bookmark exports and Firefox bookmark backups). It can import browsing history from CSV or compatible JSON files, and it can open tab URLs supplied in a JSON export or pasted one per line. The importer validates and keeps only HTTP/HTTPS addresses.

Passwords, cookies, and active sign-in sessions are not imported. They are protected by each browser and operating system, so sign in to websites again in Morrow.

## Releases

Source code and tagged app releases are maintained in [Morrow.-App](https://github.com/mrbeannnyyyy/Morrow.-App). The macOS Apple silicon DMG is attached to each GitHub release.
