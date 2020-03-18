# QRCodeTester


## QrBuilderTests

### #Transaction Amount shall only include (numeric) digits "0" to "9" and may contain a single "." character as the decimal mark even if there are no decimals. (change to default is 0)
input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | --- | 
93| 540593.00| 54|05|93.00|
008| 54048.00| 54|04|8.00|
0050.| 540550.00|54|05|50.00|
-0| 54040.00| 54|04|0.00|
-004| 54048.00| 54|04|4.00|
-0020.| 540520.00|54|05|20.00|
.654246| 54040.65|54|04|00.65|
-.007657| 54040.01|54|04|00.01|
-0..| 54040.00|54|04|00.00|
..| 54040.00|54|04|00.00|

### #Reading Amount have incorrect format (change to default is 0)

input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | ---| 
5405AA.BB| 54040.00|54|04|0.00|`ใส่ค่าที่ใช่ตัวตัวเลข แต่ตรงตาม Format Data`|
5406-AA.BB| 54040.00|54|04|0.00|`ใส่ค่าที่ใช่ตัวตัวเลข แต่ตรงตาม Format Data`|
5402AA| 54040.00|54|04|0.00|
5403-AA| 54040.00|54|05|0.00|


 ## QrReaderTests

### Reading Amount shall only include (numeric) digits "0" to "9" and may contain a single "." character as the decimal mark even if there are no decimals. (change to default is 0)
input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | --- | 
540200| 54040.00| 54 | 04 | 0.00 | --- | 
54030.1| 54040.10| 54 | 04 | 0.01 | --- | 
5402..| 54040.00| 54 | 04 | 0.00 | --- | 
5402AA| 54040.00| 54 | 04 | 0.00 | --- | 
5405AA.BB| 54040.00| 54 | 04 |0.00 | --- | 
5405AA.BB| 54040.00| 54 | 04 | 0.00 | --- | 
5405-0.00| 54040.00| 54 | 04 | 0.00 | --- | 


