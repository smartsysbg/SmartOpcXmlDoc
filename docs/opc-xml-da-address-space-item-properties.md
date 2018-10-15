#  dataType

**Description:** Item canonical data type  
**Data Type:**  *string*  
One of the following valid values must be used:

- float

- int

- unsignedInt

- long

- unsignedLong

- double

- unsginedShort

- boolean

- string

- dateTime

- anyType

- decimal

- byte

- short

- ArrayOfFloat

- ArrayOfInt

- ArrayOfUnsignedInt

- ArrayOfLong

- ArrayOfUnsignedLong

- ArrayOfDouble

- ArrayOfUnsginedShort

- ArrayOfBoolean

- ArrayOfString

- ArrayOfDateTime

- ArrayOfAnyType

- ArrayOfDecimal

- ArrayOfByte

- ArrayOfShort

#  **value** 

**Description:** Item canonical value  
__Example:__  
```xml
<value xsi:type="xsd:unsignedLong" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
```

# accessRights

**Description:** Item access rights  
**Data Type:** *string*  
One of the following valid values must be used:  

- unknown

- readable

- writable

- readWritable

#  scanRate

**Description:** This represents the fastest rate (in milliseconds) at which the server could obtain data from the underlying data source. This value generally represents the ‘best case’ or fastest RequestedSamplingRate which could be used if this item were subscribed to.
The accuracy of this value (the ability of the server to attain ‘best case’ performance) may be greatly affected by system load and other factors.  
**Data Type:** *float*

# euType

**Description:** Item EU type  
**Data Type:** *string*  
One of the following valid values must be used:

- noEnum

- analog

- enumerated


# euInfo

**Description:** If item `euType` is `enumerated` then euInfo will contain an array of strings which correspond to sequential numeric values (0, 1, 2, etc.)  
__Example:__

```xml
<string>OPEN</string> 
<string>CLOSE</string> 
<string>IN TRANSIT</string>
 etc.
``` 

**Data Type:** *ArrayOfString*

# engineeringUnits

**Description:** EU units e.g. `DEGC` or `GALLONS`  
**Data Type:** *string*


# description

**Description:** Item description e.g. “Evaporator 6 Coolant Temp”  
**Data Type:** *string*

# highEU

**Description:** Present only for `analog` data. This represents the highest value likely to be obtained in normal operation and is intended for such use as automatically scaling a bargraph display.
e.g. 1400.0  
**Data Type:** *double*

# lowEU

**Description:** Present only for `analog` data. This represents the lowest value likely to be obtained in normal operation and is intended for such use as automatically scaling a bargraph display.
e.g. -200.0  
**Data Type:** *double*

# highIR

**Description:** High instrument range. Present only for `analog` data. This represents the highest value that can be returned by the instrument.
e.g. 9999.9  
**Data Type:** *double*

# lowIR

**Description:** Low instrument range. Present only for `analog` data. This represents the lowest value that can be returned by the instrument.
e.g. -9999.9  
**Data Type:** *double*

# closeLabel

**Description:** Contact close label. Present only for `discrete` data. This represents a string to be associated with this contact when it is in the closed (non-zero) state e.g. `RUN`, `CLOSE`, `ENABLE`, `SAFE` ,etc.  
**Data Type:** *string*

# openLabel

**Description:** Contact open label. Present only for ‘discrete' data. This represents a string to be associated with this contact when it is in the open (zero) state e.g. `STOP`, `OPEN`, `DISABLE`, `UNSAFE` ,etc.   
**Data Type:** *string*

# timeZone

**Description:** The time difference (in minutes) between the item’s UTC Timestamp and the local time in which the item value was obtained.  
**Data Type:** *unsignedInt*

# minimumValue

**Description:** The smallest positive value that can be stored in the item.  
**Data Type:** *Same as the data type for the item e.g.*

```xml
<maximumValue xsi:type="xsd:unsignedLong" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">18446744073709551614</maximumValue>
```

# maximumValue

**Description:** The largest positive value that can be stored in the item.  
**Data Type:** *Same as the data type for the item e.g.*

```xml
<minimumValue xsi:type="xsd:unsignedLong" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</minimumValue>
```

# valuePrecision

**Description:** The maximum precision that can be stored in the item.  
**Data Type:** *double*
