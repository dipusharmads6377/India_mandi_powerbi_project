# Power Query Cleaning Steps

Do this once you're in Power BI Desktop with the 5 CSVs downloaded.

## 1. Import each crop CSV

`Home → Get Data → Text/CSV` → select e.g. `Onion.csv`. Repeat for all 5 files.
In the Power Query editor, rename each query to match the crop
(`Onion`, `Tomato`, `Potato`, `Wheat`, `Rice`).

## 2. Standardize columns in each query

For each query, apply:

1. **Promote headers** (if not already done automatically)
2. **Change types:**
   - `Arrival_Date` → Date
   - `Min_Price`, `Max_Price`, `Modal_Price` → Whole Number or Decimal
   - `State`, `District`, `Market`, `Commodity`, `Variety` → Text
3. **Trim & Clean** the text columns (`Transform → Format → Trim/Clean`) —
   AGMARKNET exports often have stray whitespace
4. **Remove duplicates** (`Home → Remove Rows → Remove Duplicates`) if the
   crop file has repeated arrival-date/market rows
5. **Filter out** any rows where `Modal_Price` is 0 or blank (bad government
   data entries — common in AGMARKNET exports)
6. If a `Commodity` column doesn't already exist in the file, add a **Custom
   Column** `Commodity = "Onion"` (etc.) before appending, so you can tell
   crops apart after combining

## 3. Append into one fact table

`Home → Append Queries → Append as New` → select all 5 cleaned queries →
name the result `Mandi_Prices`.

## 4. Add a Price Spread column

In `Mandi_Prices`, add a custom column:
```
Price_Spread = [Max_Price] - [Min_Price]
```
This measures how wide the quality/grading dispersion is on a given day/market.

## 5. Build a Date table

`Home → New Source → Blank Query`, then in the formula bar:
```
= Calendar(Date(2023,1,1), Date(2025,12,31))
```
Rename to `DimDate`, add columns: `Year`, `Month`, `MonthName`, `Quarter`,
`YearMonth` (for sorting). Mark it as a **Date Table** in Model view, and
relate `DimDate[Date] → Mandi_Prices[Arrival_Date]` (one-to-many).

## 6. Build a State/Market dimension (optional, cleaner model)

If you want a proper star schema: extract distinct `State`, `District`,
`Market` combinations into a `DimMarket` table, give it a surrogate key,
and relate it to `Mandi_Prices`. For a portfolio project of this size, a
single flat fact table + `DimDate` is also acceptable — mention in your
README which approach you took and why.

## 7. Close & Apply

`Home → Close & Apply`. You're now ready to write the DAX measures in
`DAX_Measures.md`.
