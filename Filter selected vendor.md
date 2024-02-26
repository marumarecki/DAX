<h3 align = "center">Filter Selected Vendor</h3>
<p>Dax formula to change title based on filter selection</p>

```DAX
Filter Selected Vendor = 
IF (
    CALCULATE (
        HASONEVALUE ( dim_Vendor[Vendor_Code] ),
        ALLSELECTED ( dim_Vendor)
    )
        = TRUE (),
    SELECTEDVALUE (dim_Vendor[Vendor_Name] ),
    "All Vendors"
)
```

