<h3 align="center"> Formula to calculate Week On Week % Change & Formula to display change in text format where can be applied in reference label with New Card Visual</h3>

<strong>Steps:</strong>

<ol>
  <li>Create first measure to retrieve WoW Change %
      <p>Calculate WoW change:</p>

      
   
    

  </li>
  <li>Create measures to get indicator arrows which can be add to text measure</li>
  <ul>
  <li>Create Arrow UP Measure
  
  ```DAX
  Indicator_Arrow_Up = UNICHAR(9650)
  ```
  </li>
  <li>Create Arrow Down Measure
  
  ```DAX
  Indicator_Arrow_Down = UNICHAR(9660) 
  ```
   </li>
   <li>Create Neutral Indicator (when change is 0%) used bullet character (dot)

   ```DAX
   Indicator_Neutral_Dot = UNICHAR(8226)
   ```
     
   </li>
    
  </ul>
  <li>Combine all above in one measure which can be use to display in KPI Card

  
```DAX
Sales_WoW_Text = 
var _text = FORMAT([WoW_Time_Series_Value],"0.0%") --format result of WoW measure as text in "0.0%" format.
var _text_return = switch(
    TRUE(),
    [WoW_Time_Series_Value] > 0, _text & " " &[Indicator_Arrow_Up],
    [WoW_Time_Series_Value] < 0, _text & " " &[Indicator_Arrow_Down],
    Indicator_Neutral_Dot)
RETURN _text_return
```

  
  </li>
</ol>
