```Dax
Unit_Volume = CALCULATE (
    FIRSTNONBLANK ( 'SKU Data'[Volume ], 1 ),
    FILTER ( ALL ( 'SKU Data' ),'SKU Data'[Material Code] = 'Sales Data'[Material_Code] )
)
```
