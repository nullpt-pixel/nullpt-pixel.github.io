# SYS//HOME — OPERATIONS MANUAL

## Quick Start

Open `index.html` in any modern browser. Single file; no server needed. localStorage persists everything across sessions automatically.

---

## Interface Overview

**Header Bar** (top)  
System title, clock, uptime counter. Double-click title to edit it.

**Editor Panel** (left)  
Write notes directly. Auto-saves to localStorage every 500ms. Plain text only.

**Links Sidebar** (right)  
Quick bookmarks. Format per line: `label | url`. Click to open. Edit in settings modal.

**Music Player** (bottom-right)  
Audio playback with seek bar, volume slider, loop toggle. Paste audio URL in settings to load a track.

**Search Modal** (triggered by Ctrl+K)  
Type query, press Enter. Routes to DuckDuckGo by default; change target in settings.

---

## Customization

### Appearance

Open **Settings** (Ctrl+,) or click gear icon.

**Theme** — dark/light  
**Effect** — crt/arcade/phosphor/vhs/gameboy/none  
**Accent Color** — amber/green/cyan/red/violet/white/orange/yellow  
**Grain/Scanlines** — toggle on/off  
**Wallpaper** — enable background image transparency  
**Background Image** — paste image URL  
**Background Dim** — opacity slider (0–1)

All settings save immediately to localStorage.

### Content

**Links**  
Edit in settings modal. One link per line. Format: `label | url`. Save automatically.

**Music**  
Paste audio file URL (mp3, wav, ogg, etc.) in settings. Hit apply. Player controls appear at bottom.

**Page Title**  
Double-click `SYS//HOME` in header to edit. Saves to localStorage.

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+K` or `Cmd+K` | Open Search Modal |
| `Ctrl+,` or `Cmd+,` | Open Settings Modal |
| `Escape` | Close All Open Modals |
| `Ctrl+Shift+D` | Unlock Debug Panel (advanced) |
| Double-click Header Title | Edit Page Title |

**Mobile**  
Long-press stats bar for 3 seconds to unlock debug panel.

---

## The Nuke Button

Located in settings modal under "Danger Zone."

**What it does:** Triggers a full-screen alert. User confirms, all data is cleared, then reloads the page.

**Variants:**
- `default` — clinical warning
- `creepypasta` — horror narrative
- `arg` — alternate reality game style
- `bsod` — Windows error parody
- `loop` — glitchy confirmation loop

---

## Debug Panel

Unlock via `Ctrl+Shift+D` (desktop) or 3-second long-press on stats bar (mobile).

### System Info Tab
Displays: user agent, viewport size, timezone, locale, network status, device memory, CPU cores, touch support, screen resolution, localStorage size, service worker status.

### Storage Tab
Live localStorage editor. View/edit all keys as JSON. Save changes; they apply immediately and reload settings.

### Performance Tab
Real-time FPS counter and JavaScript heap memory usage. Runs only while panel open.

### Error Log Tab
Captures JS console errors and warnings. Clear log with button.

### Nuke Config Tab
Advanced: set custom siren/alert sound URL for nuke variants. Debug use only.

---

## Settings Reference

All state lives in localStorage under `settings:*` keys. Reset any by deleting it and reloading page.

| Key | Default | Editable? |
|-----|---------|-----------|
| `settings:theme` | dark | Settings UI |
| `settings:effect` | crt | Settings UI |
| `settings:accent` | amber | Settings UI |
| `settings:grain` | on | Settings UI |
| `settings:scanlines` | on | Settings UI |
| `settings:wallpaper` | false | Settings UI |
| `settings:bgUrl` | (empty) | Settings UI |
| `settings:bgDim` | 0.5 | Settings UI |
| `settings:note` | (empty) | Editor Panel |
| `settings:links` | (default) | Settings UI |
| `settings:music` | (empty) | Settings UI |
| `settings:musicVolume` | 0.3 | Music Player |
| `settings:pageTitle` | SYS//HOME | Header Title |
| `settings:sirenUrl` | (empty) | Debug Panel |

**To reset everything:** Open debug panel, go to Storage tab, clear JSON, save.

---

## Offline & Caching

Service worker installed automatically on first load. Caches all assets (CSS, JS, fonts) except googleapis.com for offline access. Useful for airport wifi or dead zones.

To disable: unregister service worker in debug panel (advanced), or clear browser cache.

---

## Mobile Notes

Scaling disabled (`user-scalable=no`). Interface fixed to viewport; tap-friendly buttons. Long-press stats bar to open debug panel instead of keyboard shortcut.

Tested on Android Chrome, Safari iOS. Grain/scanline performance fine on modern devices.

---

## Limitations & Known Issues

**Android Chrome (v120–130)**  
Recording dot blinks via manual JavaScript toggle instead of CSS animation (browser regression). Functionally identical; no user-visible impact.

**localStorage Size**  
~5–10MB per domain. Editor notes + links take ~10–20KB typically; no realistic bloat concern.

**Fonts**  
Loaded from Google Fonts (preconnected). If googleapis.com is down, falls back to system monospace fonts. Not pretty, but functional.

**Wallpaper + Light Mode**  
Some theme/accent combinations may have contrast issues on light backgrounds. Adjust dim opacity if hard to read.

---

## Troubleshooting

**Settings disappeared after reload**  
localStorage was cleared (browser cache flush, incognito mode, deliberate). Reload page to reset to defaults.

**Search modal doesn't work**  
DuckDuckGo may block search from file:// URLs (local file access). Deploy to GitHub Pages or local server to test.

**Music player won't load audio**  
CORS restriction. Ensure audio file is served with permissive CORS headers or is on same origin.

**FPS counter shows low numbers**  
Expected during heavy grain/effect rendering. 60fps+ on modern hardware. Disable grain/scanlines in settings if you need performance.

**Nuke button does nothing**  
JavaScript disabled or alert() blocked. No fallback; button purely cosmetic without JS.

## That's It

Open, customize, deploy. Persists across reloads.

---

*Last Updated: Feb 2026*