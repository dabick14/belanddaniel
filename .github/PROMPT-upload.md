# CONTEXT: Guest Photo Upload Page — upload.html
# Read WEDDING-SKILL.md first. Design must match index.html exactly.

---

## TASK
Build a standalone `upload.html` guest photo upload page.
This file lives in the same repo root as `index.html` and is served at `/upload` on Vercel.
No backend. No server. Uploads go directly from the browser to Cloudinary via unsigned upload.
Single HTML file — all CSS and JS embedded.

---

## HOW CLOUDINARY UNSIGNED UPLOAD WORKS
- No server needed. The browser POSTs directly to:
  `https://api.cloudinary.com/v1_1/YOUR_CLOUD_NAME/image/upload`
- Required fields in the POST body (FormData):
  - `file` — the image file
  - `upload_preset` — the unsigned preset name (set in Cloudinary dashboard)
- The Cloud Name and Upload Preset are safe to expose in frontend code.
- Replace `YOUR_CLOUD_NAME` and `YOUR_UPLOAD_PRESET` with the couple's actual values.
  Leave them as clearly labeled placeholder constants at the top of the `<script>` block:

  ```js
  const CLOUDINARY_CLOUD_NAME = 'YOUR_CLOUD_NAME';      // e.g. 'daniel-kukua'
  const CLOUDINARY_UPLOAD_PRESET = 'YOUR_UPLOAD_PRESET'; // e.g. 'wedding_guests'
  ```

## CLOUDINARY SETUP NOTE (include as an HTML comment at top of file)
```
<!-- 
  CLOUDINARY SETUP (do this before going live):
  1. Create a free Cloudinary account at cloudinary.com
  2. Go to Settings > Upload > Upload Presets
  3. Click "Add upload preset"
  4. Set Signing Mode to "Unsigned"
  5. Set Folder to "daniel-kukua-wedding" (or any name)
  6. Save and copy the preset name
  7. Copy your Cloud Name from the Cloudinary dashboard home
  8. Replace YOUR_CLOUD_NAME and YOUR_UPLOAD_PRESET below
-->
```

---

## DESIGN REQUIREMENTS
- Must match the visual language of `index.html` exactly
- Same fonts: Cormorant Garamond + Jost (load same Google Fonts `<link>`)
- Same CSS custom properties (copy the full `:root` block)
- Same background color `var(--color-bg)`
- Same accent color `#B5A882`
- Minimal nav: just `D & K` brand (links back to `/`) and the page title
- No footer needed — just a small `← back to the wedding site` text link at the bottom

---

## PAGE LAYOUT

### Header
- Top: minimal nav bar — brand `D & K` on left (links to `/`), nothing else
- Below nav, centered:
  - Eyebrow label (Jost uppercase muted): `"daniel & kukua · june 4, 2026"`
  - Heading (Cormorant Garamond 300, large): `Share your photos`
  - Subheading (Cormorant italic, muted, ~1.2rem):
    `"Help us remember every beautiful moment of this day."`

### Upload Area
- Large dashed bordered drop zone — center of page
- Dashed border: `2px dashed var(--color-accent)`
- Background: `var(--color-bg-alt)`
- Rounded: `border-radius: 4px`
- Contents of drop zone (centered, vertically):
  - SVG camera/photo icon (line style, ~48px, accent color)
  - Primary text (Cormorant italic ~1.3rem): `"Drop your photos here"`
  - Secondary text (Jost 300 small muted): `"or click to browse"`
  - Hidden `<input type="file" accept="image/*" multiple>`
  - The entire drop zone is clickable and triggers the file input
- Drag-over state: border becomes solid, background slightly darker

### File Preview Grid
- After files are selected, show a preview grid below the drop zone
- Grid: 3 columns on desktop, 2 on mobile
- Each preview tile:
  - `object-fit: cover` thumbnail
  - File name below in Jost 300 small truncated
  - Small `×` remove button (top-right corner of tile)
  - Upload status overlay: idle / uploading (progress bar) / success ✓ / error ✗

### Upload Button
- Below the preview grid
- Outlined Jost button (matches skill's button style):
  `border: 1px solid var(--color-text-primary); padding: 0.85rem 2.5rem; background: transparent`
- Label: `Upload photos`
- Loading state: label changes to `Uploading...`, button disabled
- Hidden until at least one file is selected

### Success State
- After all files upload successfully, replace the upload area with:
  - Large Cormorant italic: `"Thank you! 🤍"`
  - Body text: `"Your photos have been received. Daniel & Kukua will treasure them."`
  - Small link: `Upload more photos` (resets the UI)

### Error Handling
- Per-file errors shown on the tile (red `✗`, tooltip with error message)
- If all fail: show a gentle error banner in Jost below the button

---

## UPLOAD LOGIC (JavaScript)

```
1. User selects files via click or drag-and-drop
2. Files appear in preview grid (use FileReader for thumbnails)
3. User clicks "Upload photos"
4. For each file:
   a. Create a FormData object
   b. Append file, upload_preset, cloud_name folder tag
   c. POST to https://api.cloudinary.com/v1_1/{CLOUD_NAME}/image/upload
   d. Show per-file progress (use XHR with onprogress, not fetch, for progress events)
   e. On success: mark tile with green ✓
   f. On error: mark tile with red ✗ and log the error message
5. When all complete: show success state if no errors, or partial error state
```

Use `XMLHttpRequest` (not `fetch`) so you can track `upload.onprogress` per file.
Upload files in parallel (all at once, not sequentially).

### Progress bar per tile
```js
xhr.upload.onprogress = (e) => {
  if (e.lengthComputable) {
    const pct = Math.round((e.loaded / e.total) * 100);
    // update the tile's progress bar width
  }
};
```

---

## OPTIONAL GUEST NAME FIELD
- Above the drop zone, a simple optional text input:
  - Label (Jost 300 small): `Your name (optional)`
  - Input styled to match site: `border: none; border-bottom: 1px solid var(--color-border); background: transparent; font-family: Cormorant Garamond`
- If filled, append as a Cloudinary tag: `context: { caption: guestName }`
  by adding to FormData: `formData.append('context', 'caption=' + guestName)`
  This lets the couple filter/identify photos by guest name in Cloudinary.

---

## FILE VALIDATION
- Accept: images only (`image/*`)
- Max file size: 20MB per file — show friendly error if exceeded:
  `"This file is too large. Please upload photos under 20MB."`
- Max files at once: 20 — show gentle warning if exceeded
- Validate before upload, not after

---

## TECHNICAL REQUIREMENTS
- Single HTML file, all CSS + JS embedded
- Same Google Fonts `<link>` as index.html
- Full `:root` CSS variables block (copy from index.html)
- No external JS libraries
- Mobile-first, fully responsive
- Works on iOS Safari (test: `input[type=file]` capture attribute is NOT needed — guests upload from camera roll)
- Drag and drop events: `dragover`, `dragleave`, `drop` on the drop zone
- `URL.createObjectURL()` for thumbnails (faster than FileReader for preview)
- Clean up object URLs after upload with `URL.revokeObjectURL()`
