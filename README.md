# Bedrock UI Studio v8

Mobile-friendly offline-first editor for planning Minecraft Bedrock UI projects.

## Files
- `index.html` — structure and editor panels
- `styles.css` — layout, theme, responsive styling
- `app.js` — editor logic, project storage, texture generation and exports

## Run locally
Keep all three files in the same folder and open `index.html` in a modern browser. For reliable local file handling on Android, use Acode preview or a local static server.

## Included in v8
- Collapsible nested project tree; select folders as upload/create destinations
- Create text files and folders, upload/preview PNG files, rename selected files and delete a selected folder with its contents
- Dedicated chest-layout starter controls for title, columns, rows, slot size/gap and colors
- Server Form Builder drafts JavaScript using ActionFormData, MessageFormData or ModalFormData
- Optional editor-only UI tags on elements
- Existing hover/pressed color generation and separate texture outputs
- Auto-generated behavior/resource pack manifests and `.mcaddon` export

## Important limits
This is a client-side starter editor, not a full Bedrock JSON UI runtime. Generated chest layouts are visual design starters and do not automatically replace the vanilla chest screen. Validate control schemas, texture paths and manifests against the exact Bedrock version you target before using the exported add-on. Project contents stay in browser storage until you export them.
