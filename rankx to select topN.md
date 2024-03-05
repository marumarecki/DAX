<h3>Parameter table:</h3>

```DAX
TopN = GENERATESERIES(0, 5, 1)
```

<h3>Rank in descending order:</h3>

```DAX
topN = 
 Var weekrank = RANKX(ALL('Sales Data'[FinancialWeekNumber]), SUMX(RELATEDTABLE('Sales Data'), 'Sales Data'[HDSalesQuantity_in_BOM]))
 VAR SelectedTopN = SELECTEDVALUE('TopN'[TopN])
 RETURN
 SWITCH(
    TRUE(),
    SelectedTopN = 0, 1,
    weekrank <= SelectedTopN, 1,
    0
 )
```

<h3>Rank in ascending order:</h3>

```DAX
bottomN = 
 Var weekrank = RANKX(ALL('Sales Data'[FinancialWeekNumber]), SUMX(RELATEDTABLE('Sales Data'), 'Sales Data'[HDSalesQuantity_in_BOM]),,ASC)
 VAR SelectedTopN = SELECTEDVALUE(BottomN[BottomN])
 RETURN
 SWITCH(
    TRUE(),
    SelectedTopN = 0, 1,
    weekrank <= SelectedTopN, 1,
    0
 )
```
