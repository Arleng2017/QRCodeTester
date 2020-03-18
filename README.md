# QRCodeTester


## QrBuilderTests
### Transaction Amount shall only include (numeric) digits "0" to "9" and may contain a single "." character as the decimal mark even if there are no decimals. (change to default is 0)
INPUT     |      result | 
--- | --- | 
1 | 2 
0| 54040.00
01| 54041.00
001| 54041.00
001| 54041.00
010| 5404510.00
0010| 5404510.00
0010.| 5404510.00
0010.00| 5404510.00
-0| 54040.00
-01| 54041.00
-001| 54041.00
-001| 54041.00
-010| 5404510.00
-0010| 5404510.00
-0010.| 5404510.00
-0010.00| 5404510.00
.00| 54040.00
-.00| 54040.00
-0..| 54040.00
..| 54040.00

### Reading Amount have incorrect format (change to default is 0)

INPUT     |      result | 
--- | --- | 
5405AA.BB| 54040.00
5402AA| 54040.00
5403-AA| 54040.00


###  The Transaction Currency shall conform to [ISO 4217] and shall contain the 3-digit numeric representation of the currency.
INPUT | result | 
--- | --- | 
5303thb|5303THB
thb|5303THB
THB|5303THB
  

 ## QrReaderTests

### Reading Amount shall only include (numeric) digits "0" to "9" and may contain a single "." character as the decimal mark even if there are no decimals. (change to default is 0)
INPUT | result | 
--- | --- | 
5401.| "54040.00
540200| "54040.00
5403000| "54040.00
54030.0| "54040.00
5402..| "54040.00
5402AA| "54040.00
5405AA.BB| "54040.00

 ### Reading Amount have incorrect format (change to default is 0)

INPUT | result | 
--- | --- | 
5405AA.BB| 54040.00
5405-0.00| 54040.00
54011| 54040.00
540200| 54040.00
5403000| 54040.00