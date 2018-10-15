# Overview
![](./media/image58.png)

# HdaReadRaw

```csharp
HdaItemValueCollection[] HdaReadRaw(
           HdaTime startTime,
           HdaTime endTime,
           int maxValues,
           bool includeBounds,
           HdaItemIdentifier[] items)
```

![](./media/image59.png)
![](./media/image60.png)
![](./media/image61.png)
![](./media/image62.png)
![](./media/image63.png)
![](./media/image64.png)
![](./media/image65.png)
![](./media/image66.png)
![](./media/image67.png)
![](./media/image68.png)
![](./media/image69.png)

# HdaReadProcessed

```csharp
HdaItemValueCollection[] HdaReadProcessed(HdaTime startTime,
            HdaTime endTime,
            decimal resampleInterval,
            HdaItem[] items)
```

![](./media/image70.png)

# HdaBrowse

```csharp
HdaBrowseElement[] HdaBrowse(HdaItemIdentifier item)
```

![](./media/image71.png)
![](./media/image72.png)
![](./media/image73.png)

# HdaGetStatus

```csharp
HdaServerStatus HdaGetStatus(HdaItemIdentifier item)
```

![](./media/image74.png)
![](./media/image75.png)

*``Remarks:`` HdaItemIdentifier argument is used to navigate to the OPC HDA
server of which to get the status. If item identifier is null, status of
the plugin will be returned.*

# HdaGetAggregates

```csharp
HdaAggregate[] HdaGetAggregates(HdaItemIdentifier item)
```

![](./media/image76.png)
![](./media/image77.png)

# HdaReadAtTime

```csharp
HdaItemValueCollection[] HdaReadAtTime(DateTime[] timestamps, HdaItemIdentifier[] items)
```

*``Remarks:`` Not supported by all OPC HDA servers.*

```csharp
public class HdaAggregateID {
        public const int NOAGGREGATE = 0;
        public const int INTERPOLATIVE = 1;
        public const int TOTAL = 2;
        public const int AVERAGE = 3;
        public const int TIMEAVERAGE = 4;
        public const int COUNT = 5;
        public const int STDEV = 6;
        public const int MINIMUMACTUALTIME = 7;
        public const int MINIMUM = 8;
        public const int MAXIMUMACTUALTIME = 9;
        public const int MAXIMUM = 10;
        public const int START = 11;
        public const int END = 12;
        public const int DELTA = 13;
        public const int REGSLOPE = 14;
        public const int REGCONST = 15;
        public const int REGDEV = 16;
        public const int VARIANCE = 17;
        public const int RANGE = 18;
        public const int DURATIONGOOD = 19;
        public const int DURATIONBAD = 20;
        public const int PERCENTGOOD = 21;
        public const int PERCENTBAD = 22;
        public const int WORSTQUALITY = 23;
        public const int ANNOTATIONS = 24;
    }
```