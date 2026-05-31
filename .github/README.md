# daniel-kukua-wedding

Wedding website for Daniel Dadzie & Belfrieda Kukua Asamoah · June 4, 2026

---

## Repo Structure

```
daniel-kukua-wedding/
├── index.html          ← Main wedding site  (build using PROMPT-index.md)
├── upload.html         ← Guest photo upload (build using PROMPT-upload.md)
├── WEDDING-SKILL.md    ← Reusable design system for all wedding sites
├── PROMPT-index.md     ← Full Copilot prompt for index.html
├── PROMPT-upload.md    ← Full Copilot prompt for upload.html
└── README.md           ← This file
```

---

## How to Build

Each `.md` prompt file is a self-contained context file for GitHub Copilot (or any AI coding assistant).

1. Open `PROMPT-index.md` → paste into Copilot → generates `index.html`
2. Open `PROMPT-upload.md` → paste into Copilot → generates `upload.html`

Both prompts reference `WEDDING-SKILL.md`. Include the skill contents at the top of each prompt for best results, or point Copilot to the file explicitly.

---

## Deployment (Vercel)

1. Push repo to GitHub
2. Import repo in Vercel dashboard
3. Framework: **Other** (static)
4. Root directory: `/`
5. No build command needed

Vercel serves static files by path automatically:
- `/` → `index.html`
- `/upload` → `upload.html`

No `vercel.json` config needed for this structure.

---

## Cloudinary Setup (before going live)

1. Create a free account at [cloudinary.com](https://cloudinary.com)
2. Dashboard → Settings → Upload → Upload Presets → Add upload preset
3. Signing Mode: **Unsigned**
4. Folder: `daniel-kukua-wedding`
5. Save — copy the preset name
6. Copy your **Cloud Name** from the Cloudinary dashboard home page
7. Open `upload.html` and replace:
   ```js
   const CLOUDINARY_CLOUD_NAME = 'YOUR_CLOUD_NAME';
   const CLOUDINARY_UPLOAD_PRESET = 'YOUR_UPLOAD_PRESET';
   ```

Free tier: 25GB storage + 25GB bandwidth/month — more than sufficient for one wedding.

---

## Custom Domain

In Vercel dashboard → Domains → add your custom domain (e.g. `danielandkukua.com`).
The `/upload` path works automatically on the custom domain — no extra config.

---

## QR Codes

Generate two QR codes pointing to:
- **Main site:** `https://yourdomain.com`
- **Photo upload:** `https://yourdomain.com/upload`

Recommended free QR generator: [qr.io](https://qr.io) or [qrcode-monkey.com](https://qrcode-monkey.com)
Style the upload QR in accent color `#B5A882` if the generator supports it.

---

## Reusing WEDDING-SKILL.md for Other Couples

`WEDDING-SKILL.md` is couple-agnostic. For a new wedding:
1. Copy `WEDDING-SKILL.md` into the new repo
2. Write a new `PROMPT-index.md` with the new couple's details
3. Write a new `PROMPT-upload.md` (mostly reusable — just update names/dates/Cloudinary folder)
4. The skill's design system handles all typography, color, and layout decisions
