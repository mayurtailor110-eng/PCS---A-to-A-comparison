# PCS Apple-to-Apple Comparison Dashboard

A self-contained web dashboard for evaluating BESS Power Conversion System (PCS) vendors on technical, performance, compliance and commercial parameters. Runs entirely in the browser — no server, no database.

**Live site:** `https://<your-username>.github.io/pcs-dashboard/`

---

## What's in this repo

| File | What it is |
|---|---|
| `index.html` | The dashboard. Loads `PCS_Master_Data.csv` automatically. |
| `PCS_Master_Data.csv` | The data the dashboard reads. **This is the only file you re-upload to update the dashboard.** |
| `PCS_Demo_Data.csv` | Sample dataset (3 fictional vendors, one critical failure) for testing. |
| `PCS_Comparison_Master.xlsx` | Edit your data here comfortably, then convert to CSV. |
| `convert.html` | Drop the Excel here → downloads a fresh `PCS_Master_Data.csv`. |

---

## One-time setup (website only — no commands needed)

1. Create a new GitHub repository named **`pcs-dashboard`** (Public).
2. Click **Add file → Upload files**, drag in **all files from this folder**, and commit.
3. Go to **Settings → Pages**.
4. Under **Source**, choose **Deploy from a branch**, pick **`main`** / **`/ (root)`**, and click **Save**.
5. Wait ~1 minute. Your dashboard is live at `https://<your-username>.github.io/pcs-dashboard/`.

---

## Updating the data (the everyday workflow)

You never touch the HTML. Just refresh the CSV:

1. Open **`PCS_Comparison_Master.xlsx`**, edit values in the **PCS_Master_Data** sheet (yellow column).
2. Open **`convert.html`** (double-click), drop the Excel in → it downloads a fresh **`PCS_Master_Data.csv`**.
3. On GitHub: open the repo → **Add file → Upload files** → drop the new `PCS_Master_Data.csv` (it replaces the old one) → **Commit**.
4. The live dashboard updates within ~1 minute.

> Prefer editing the CSV directly? You can — just keep the column headers unchanged and re-upload it.

---

## How the dashboard scores vendors

- Each parameter is scored 0–10, weighted by category, and normalized to a final score out of 100.
- **Compliance:** Higher-Better → value ≥ requirement = PASS · Lower-Better → value ≤ requirement = PASS · Range → vendor window must cover the required window · Boolean → YES vs required YES.
- **Missing data** shows as **N/A** or **Data Pending** and is *never* counted as pass or fail. The Data Quality section shows each vendor's completeness so nobody scores well by leaving fields blank.
- **Critical parameters** (marked `Critical=YES`) that FAIL trigger **CRITICAL NON-COMPLIANCE** — that vendor cannot rank first regardless of score.

---

## Notes

- The dashboard ships pointed at real supplier data. `PCS_Demo_Data.csv` is clearly marked sample data — replace with verified datasheet values before making procurement decisions.
- Everything works offline too: just open `index.html` directly and upload a CSV with the drag-and-drop area.
- **Is your data confidential?** A public GitHub Pages site is open to anyone with the link. If the data is sensitive, use a **private repo** with Cloudflare Pages (free, supports access control) instead of public GitHub Pages.
