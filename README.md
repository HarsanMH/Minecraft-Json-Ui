# Bedrock UI Studio v8.1 — Button Fix

Mobile-friendly offline-first editor for planning Minecraft Bedrock UI projects.

## Files
- `index.html` — page structure
- `styles.css` — responsive styling
- `app.js` — editor logic and project storage

## Fixes in v8.1
- Browser storage is guarded: when local storage is unavailable, it should no longer stop startup before the page buttons are wired up.
- New-project and sample-project flows open the editor directly rather than requiring a reload.
- Saved project cards open projects directly in the current page.
- Project-tree file buttons now display their filenames.
- Newly created text files use the same structure as other project files.
- Export handles older projects with text files stored as plain strings.
- Unhandled JavaScript errors are shown in the page instead of failing completely silently.

## Run locally
Keep all three main files in one folder and open `index.html` in a modern browser, or use Acode preview. If you use GitHub Pages, upload/replace `index.html`, `styles.css`, and `app.js` in the same directory and refresh the site without cache.

## Important limits
This is an offline-first starter editor, not a full Bedrock JSON UI runtime. Generated chest layouts are visual starters and do not automatically replace the vanilla chest screen. Server Form Builder generates a JavaScript draft that still needs to be connected to a real event. Validate JSON UI controls, texture paths, manifests and Script API versions against the exact Bedrock version you target.

## Testing note
The JavaScript syntax check passes and static HTML ID references were audited. Automated browser interaction testing could not be completed in this environment, and the pack has not been tested in Minecraft in this pass. Treat this as a targeted fix build rather than a guarantee that every feature is bug-free.
