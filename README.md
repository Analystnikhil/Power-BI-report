# Power-BI-report
How to calculate Year on Year (YoY) Growth? - Estimated Sales
Hi All - I am trying to calculate YoY Sales Growth for a particular year 

 

I have the following information:

 

Sales Last Year for 2020 was 28.182M
YoY Growth Rate calculation is 44%
Expected Sales budget results for 2021 should be 28.18M * 1.44 = 40.58M
 

Please see measures calculated below:

 

Total Sales = SUMX(Sales , Sales[Quantity] * RELATED( ‘Product’[Current Price] ) )
Sales LY =  CALCULATE( [Total Sales] , DATEADD( Dates[Date] , -1, YEAR ) )
Sales TY vs LY = IF( ISBLANK( [Sales LY] ) , BLANK() , [Total Sales] - [Sales LY] )
YoY Sales Growth  = DIVIDE( [Sales TY vs LY ] , [Sales LY] , 0 )
How do I calculate the Estimated Sales for 2020.

 

An easier option would be

Estimated Sales  =  [Sales LY] * 1.44 however I am keen to ensure that no hard numbers exists in my reports, and make it dynamic

 

I also tried this measure: ( Did not work)

Sales Budget = [Sales LY] * ( 1 + [YoY Sales Growth] ) 
