# 3ds Media Manager

A single HTML file that lets you browse, sort, and star screenshots (and video clips) off your 3DS/DS SD card, right in your browser. No install, no upload, no server — just open the file and point it at your SD card.

## Why this exists

If you've ever used a custom firmware screenshot tool (Luma, Comet, nds-bootstrap) you know the pain: your SD card ends up full of cryptically-named `.bmp`/`.jpg` files scattered across a few different folders, and there's no easy way to actually *look* through them without pulling every file onto your PC first. This is basically a little gallery app that understands those folder structures and just... shows you your screenshots, properly grouped, with dates and 3D support and everything.

## What it does

- **Reads straight off the SD card** using the File System Access APIs — you pick the root of the card and it automatically finds:
  - `luma/screenshots` (Luma3DS screenshots, including top-screen + bottom-screen pairs)
  - `3ds/Comet/ds_screenshots` (DS screenshots)
  - `_nds/nds-bootstrap/screenshots.tar` (raw nds-bootstrap screenshot slots)
  - `DCIM` (actual Nintendo 3DS camera photos and videos)
- **Sorts stuff into tabs** — 3DS / DS / Camera — so you're not scrolling through everything at once
- **Understands 3D screenshots** — if a shot has a top-left and top-right frame, you can view it as a red/cyan anaglyph or side-by-side cross-eye pair
- **Handles 3D camera photos too** — the 3DS camera saves a `.MPO` alongside the `.JPG` for any photo taken in 3D mode. This app decodes the MPO's two stereo frames on the fly so you can view those photos as an anaglyph or cross-eye pair too (you won't see the MPO itself cluttering the grid)
- **Plays back `.AVI` clips** from the 3DS camera, frame by frame, in browser — no plugins
- **Merge & download** — stick a top and bottom screen together into one PNG
- **Star your favorites** (saved locally, so it remembers between sessions) and filter down to just starred stuff
- **Slideshow mode** if you just want to sit back and watch

## Using it

Just open the [live page](https://codymkw.github.io/3dsMediaManager) in any modern browser, click "Open SD card", and select the **root** of the SD card, not a subfolder.

That's it, no download needed. Everything happens locally in the tab — nothing ever leaves your machine, even though it's running off GitHub Pages.

If you've only got the raw `screenshots.tar` from nds-bootstrap and not the whole card, there's a separate "open that file instead" option for just that.

## Heads up

- This is a fan-made tool, not affiliated with Nintendo in any way
- It only reads the specific folders listed above — it doesn't touch anything else on your card
- "Remove from view" just hides an item from the current session, it doesn't delete anything off your SD card
- Some AVI codecs (anything that isn't Motion-JPEG or raw/uncompressed) can't be decoded in a browser — you'll get a friendly error and a download link instead of a crash

## Known limitations

- No mobile support really — this leans on desktop browser file APIs
- Huge SD cards with thousands of screenshots will take a sec to load since everything's processed client-side

---

Feel free to fork/poke at it. PRs and issues welcome if you find something broken on your setup.
