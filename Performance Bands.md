Measure to calculate count of vendors falling in certain performance bracket or if one vendor is selected number of weeks this vendor was in certain performance bracket.

```DAX
OTIF_BANDS v.2 = 
VAR vendor = IF
(HASONEVALUE(dim_otif_band[Min_Value]),
 COUNTROWS(FILTER(DISTINCT(vw_OTIF_SKU[Vendor]), vw_OTIF_SKU[OTIF%]>=VALUES(dim_otif_band[Min_Value])&& [OTIF%]<=VALUES(dim_otif_band[Max_Value]) ) )
 , COUNTROWS(vw_OTIF_SKU) )
 VAR week =  IF
(HASONEVALUE(dim_otif_band[Min_Value]),
 COUNTROWS(FILTER(DISTINCT(vw_OTIF_SKU[PODueWeek]), vw_OTIF_SKU[OTIF%]>=VALUES(dim_otif_band[Min_Value])&& [OTIF%]<=VALUES(dim_otif_band[Max_Value]) ) )
 , COUNTROWS(vw_OTIF_SKU) )
 RETURN 
 IF (
    CALCULATE (
        HASONEVALUE ( vw_OPTIC_VendorMasterdata[VendorSearch] ),
        ALLSELECTED ( vw_OPTIC_VendorMasterdata )
    )
        = TRUE (),
        week,
        vendor)
```
