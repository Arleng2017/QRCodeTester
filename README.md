# QrBuilderTests

## #Transaction Amount shall only include (numeric) digits "0" to "9" and may contain a single "." character as the decimal mark even if there are no decimals. (change to default is 0)
### 📌Normal
input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | --- | 
93| 540593.00| 54|05|93.00|
008| 54048.00| 54|04|8.00|
0050.| 540550.00|54|05|50.00|
050.34633| 540550.35|54|05|50.35|
-0| 54040.00| 54|04|0.00|
-004| 54048.00| 54|04|4.00|
-0020.| 540520.00|54|05|20.00|
.654246| 54040.65|54|04|0.65|


## #Transaction Amount have incorrect format (change to default is 0)

### 📌incorrect

input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | ---| 
-.007657| 54040.01|54|04|0.01|
-0..| 54040.00|54|04|0.00|
..| 54040.00|54|04|0.00|
5405AA.BB| 54040.00|54|04|0.00|`ใส่ค่าที่ใช่ตัวตัวเลข แต่ตรงตาม Format Data`|
5406-AA.BB| 54040.00|54|04|0.00|`ใส่ค่าที่ใช่ตัวตัวเลข แต่ตรงตาม Format Data`|
5402AA| 54040.00|54|04|0.00|
5403-AA| 54040.00|54|05|0.00|


 # QrReaderTests

## #Reading Amount shall only include (numeric) digits "0" to "9" and may contain a single "." character as the decimal mark even if there are no decimals. (change to default is 0)

###  📌Normal

input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | --- |
5400| 54040.00| 54 | 04 | 0.00 | --- |  
54014| 54044.00| 54 | 04 | 4.00 | --- | 
540200| 54040.00| 54 | 04 | 0.00 | --- | 
54030.1| 54040.10| 54 | 04 | 0.01 | --- | 
54040.78| 54040.78| 54 | 04 | 0.78 | --- | 



### 📌incorrect
input|result | Tax ID | Data Length| Data|Detail|
--- | --- | --- | --- | --- | --- | 
5402..| 54040.00| 54 | 04 | 0.00 | --- | 
5402AA| 54040.00| 54 | 04 | 0.00 | --- | 
5405AA.BB| 54040.00| 54 | 04 |0.00 | --- | 
5405AA.BB| 54040.00| 54 | 04 | 0.00 | --- | 
5405-0.00| 54040.00| 54 | 04 | 0.00 | --- | 


## # 2 or more same id on same qr code (used last)

###  📌Normal
input|data1 |  data2 | data3 | data4|data5|data6|
--- | --- | --- | --- | --- | --- | --- |
0000000201| 000201 | --- | --- | --- | --- | --- |
6303DES6304ABCD|6304ABCD | --- | --- | --- | --- | --- |
0002015802EN53037645802TH | 000201 | 5303764 | 5802TH |--- | --- | --- | 
0002005802DM5406123.450002015802TH540445.50 | 000201 | 5802TH | 540445.50 | --- | --- | --- |

### 📌incorrect
input|data1 |  data2 | data3 | data4|data5|data6|Detail|
--- | --- | --- | --- | --- | --- | --- |--- |
00000000| Null | --- | --- | --- | --- | --- |`0000 ไม่มีดาต้า`
0002010000| 000201 | --- | --- | --- | --- | --- |`0000 ไม่มีดาต้า`
540599.995405AA.AA|540599.99| --- | --- | --- |--- | --- |`5405AA.AA data ตัวหลังผิด`