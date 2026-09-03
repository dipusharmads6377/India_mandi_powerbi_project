# Getting the Raw Data

This project uses the **Indian Agricultural Mandi Prices (2023–2025)** dataset,
built from the Government of India's AGMARKNET open data.

## Step 1 — Download from Kaggle (works fine from your phone)

1. Go to:
   `https://www.kaggle.com/datasets/arjunyadav99/indian-agricultural-mandi-prices-20232025`
2. Sign in (or create a free Kaggle account — needed to download).
3. Tap **Download** (top right) — Kaggle will zip the crop-wise CSV files
   (Onion, Tomato, Potato, Wheat, Rice).
4. Save the zip to your phone, then extract it (most Android file managers /
   iOS Files app can unzip directly; or use an app like "ZArchiver" on Android).

You'll end up with one CSV per crop. Typical AGMARKNET-schema columns are:

| Column | Description |
|---|---|
| `State` | State where the mandi is located |
| `District` | District |
| `Market` | Mandi/market name |
| `Commodity` | Crop (Onion, Tomato, Potato, Wheat, Rice) |
| `Variety` | Crop variety |
| `Arrival_Date` | Date of price reporting |
| `Min_Price` | Minimum price (₹/quintal) |
| `Max_Price` | Maximum price (₹/quintal) |
| `Modal_Price` | Most common traded price (₹/quintal) |

Check the actual header row after download — Kaggle re-uploads sometimes rename
columns slightly (e.g. `min_price` vs `Min Price`). Adjust the Power Query steps
in `Power_Query_Cleaning_Steps.md` to match whatever you actually see.

## Step 2 — Combine the 5 CSVs (optional but recommended)

Each crop file is small. Once you're on a machine with Power BI Desktop, it's
easiest to import each CSV as its own query, then **Append** them into one
`Mandi_Prices` table with the `Commodity` column already distinguishing them
(this is covered in `Power_Query_Cleaning_Steps.md`).

## Step 3 — Move the files

Put the 5 CSVs (or the combined one) somewhere you can point Power BI Desktop
at later — a cloud folder (Google Drive/OneDrive) works well since you're
phone-only until you get desktop access; that way the files are ready the
moment you sit down at a PC.
