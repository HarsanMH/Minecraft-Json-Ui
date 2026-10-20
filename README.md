# Bedrock UI Studio v8.2 — Button Fix

Mobile-friendly offline-first editor for planning Minecraft Bedrock UI projects.

## Files
- `index.html` — page structure
- `styles.css` — responsive styling
- `app.js` — editor logic and project storage

## Fixes in v8.2
**Main bug — every button was dead.** `app.js` called `applyInput('propTag', …)` for an input that does not exist in `index.html`. That threw a `TypeError` during startup, so the script stopped half-way and the Home/editor buttons further down were never wired up. `applyInput` now skips a missing field, so startup completes.

Other bugs found and fixed while auditing:
- **Project files lost on reload:** text files in Project Storage (generated server-form script, manifests, files you created or uploaded) and custom folders were not restored after refreshing the page, and uploaded PNGs dropped out of the export. They are now restored.
- **Import could overwrite another saved project:** importing a project JSON while a different saved project was active replaced that saved project's data. Import now creates its own entry. It also no longer carries textures/files over from the previous project, and clears undo history (undo after an import would have pointed at missing textures).
- **New project / Open sample did not appear under "Saved on this device"** until you pressed Save project or reloaded. They now get saved entries straight away.
- **Opening a saved project / creating a project** left stale file tabs and editor text from the previous project. The tabs and editor are reset.
- **Undo after a plain tap:** tapping an element on the canvas added an empty undo step. An undo step is now recorded only when the element actually moves or resizes.
- **Duplicate files in the exported packs** (same path added from two places, e.g. a button texture and a Storage upload) are now de-duplicated; the file you uploaded manually wins.
- The "Selected: …" caption under the canvas is cleared when nothing is selected.
- Storage buttons no longer relabel themselves to "Apply JSON" / "Export JSON files" on load (they save/export any project file).

## Run locally
Keep all three main files in one folder and open `index.html` in a modern browser, or use Acode preview. If you use GitHub Pages, upload/replace `index.html`, `styles.css`, and `app.js` in the same directory and refresh the site without cache.

## Important limits
This is an offline-first starter editor, not a full Bedrock JSON UI runtime. Generated chest layouts are visual starters and do not automatically replace the vanilla chest screen. Server Form Builder generates a JavaScript draft that still needs to be connected to a real event. Validate JSON UI controls, texture paths, manifests and Script API versions against the exact Bedrock version you target. The manifests pin `@minecraft/server` 2.9.0 and `@minecraft/server-ui` 2.0.0; check these against the version your game supports.

## Testing note
Tested in headless Chromium (Playwright) at desktop (1280 px) and phone (390 px) widths: 70 automated checks covering the Home screen, all five templates, every editor/inspector/storage/server-form/chest button, canvas drag + resize, undo/redo, save/import/export, reload persistence, and no JavaScript errors in the console. The exported `.mcaddon` was checked for zip integrity, valid manifests, no duplicate entries, and that every texture referenced by the layout JSON exists in the pack. The pack has **not** been tested inside Minecraft, and real-device touch behaviour (e.g. Acode preview) was not tested.
