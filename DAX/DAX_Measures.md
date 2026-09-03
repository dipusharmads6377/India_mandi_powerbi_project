# DAX Measures

Create these in a dedicated `_Measures` table (Model view → New Table →
`_Measures = {BLANK()}`, delete the placeholder column, keep it as a home
for all measures — good practice for a portfolio project, shows model hygiene).

## Core price measures

```DAX
Avg Modal Price =
AVERAGE ( Mandi_Prices[Modal_Price] )
```

```DAX
Avg Min Price =
AVERAGE ( Mandi_Prices[Min_Price] )
```

```DAX
Avg Max Price =
AVERAGE ( Mandi_Prices[Max_Price] )
```

```DAX
Avg Price Spread =
AVERAGE ( Mandi_Prices[Price_Spread] )
```

## Time intelligence

```DAX
Modal Price MoM % =
VAR CurrentAvg = [Avg Modal Price]
VAR PrevAvg =
    CALCULATE (
        [Avg Modal Price],
        DATEADD ( DimDate[Date], -1, MONTH )
    )
RETURN
    DIVIDE ( CurrentAvg - PrevAvg, PrevAvg )
```

```DAX
Modal Price YoY % =
VAR CurrentAvg = [Avg Modal Price]
VAR PrevAvg =
    CALCULATE (
        [Avg Modal Price],
        SAMEPERIODLASTYEAR ( DimDate[Date] )
    )
RETURN
    DIVIDE ( CurrentAvg - PrevAvg, PrevAvg )
```

## Volatility (a key insight for commodity prices)

```DAX
Price Volatility (StdDev) =
STDEV.P ( Mandi_Prices[Modal_Price] )
```

```DAX
Price Volatility % =
DIVIDE ( [Price Volatility (StdDev)], [Avg Modal Price] )
```

## Ranking / comparison

```DAX
Rank State by Avg Price =
RANKX (
    ALL ( Mandi_Prices[State] ),
    [Avg Modal Price],
    ,
    DESC
)
```

```DAX
Price vs National Avg % =
VAR NationalAvg =
    CALCULATE ( [Avg Modal Price], ALL ( Mandi_Prices[State] ) )
RETURN
    DIVIDE ( [Avg Modal Price] - NationalAvg, NationalAvg )
```

## Volume / coverage context

```DAX
Reporting Days =
DISTINCTCOUNT ( Mandi_Prices[Arrival_Date] )
```

```DAX
Active Markets =
DISTINCTCOUNT ( Mandi_Prices[Market] )
```

---

**Note on interpretation:** these are wholesale mandi prices, not retail —
useful for framing insights around traders/farmers rather than consumers.
Mention that distinction explicitly in your README or report notes; it
signals you understood the dataset rather than treating it as generic
"sales data."
