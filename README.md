# IEM Quality Check — Excel Add-in

AI-powered curriculum classifier that runs inside Excel as a task pane.
Drop a university curriculum PDF in, get classifications written directly into a new sheet.

---

## Files

| File | Purpose |
|------|---------|
| `taskpane.html` | The add-in UI + all logic (PDF extraction, Claude API, Excel writing) |
| `commands.html` | Required stub file for the manifest |
| `manifest.xml`  | Tells Excel about the add-in |

---

## Deployment (GitHub Pages — free, 5 minutes)

1. **Create a new GitHub repo** — name it `iem-excel-addin` (public)

2. **Upload all files** from this folder to the repo root

3. **Enable GitHub Pages**
   - Go to repo Settings → Pages
   - Source: Deploy from branch → main → / (root)
   - Save. Your URL will be: `https://YOUR-USERNAME.github.io/iem-excel-addin`

4. **Update the manifest**
   - Open `manifest.xml`
   - Replace every instance of `YOUR-HOSTING-URL` with your actual GitHub Pages URL
   - Commit the updated manifest

---

## Loading the Add-in in Excel

### Excel Desktop (Windows)
1. Open Excel
2. Go to **Insert → Add-ins → My Add-ins → Upload My Add-in**
3. Browse to `manifest.xml` and upload
4. The "IEM Quality Check" button will appear in the **Home** tab ribbon

### Excel on the Web (Office 365)
1. Open any workbook at office.com
2. Go to **Insert → Add-ins → Upload My Add-in**
3. Upload `manifest.xml`

---

## Usage

1. Open one of the university review `.xlsx` files
2. Click **IEM Quality Check** in the Home ribbon
3. The task pane opens on the right
4. (Optional) Type the university name
5. Drop the curriculum PDF into the upload zone
6. Click **Analyze & Fill Sheet →**
7. A new **"AI Review"** sheet is created with all courses classified
   - Green rows = clean
   - Orange rows = flagged for human review
   - "Validated?" column left empty for the reviewer to fill

---

## Notes

- Uses **Claude Haiku** (cheapest model, sufficient for classification)
- API key is handled by the Anthropic proxy — no key needed in the code
- Processes up to 25 PDF pages per run
- Cost per run: approximately $0.001 (fractions of a cent)
- Credits expire 1 year from purchase — buy the minimum $5 to start(anthropic currently gives 5 bucks in credits for free)
- Set a spending limit in console.anthropic.com to avoid any surprises
