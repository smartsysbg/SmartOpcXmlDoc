# Extracting Statistics Using HDA Feature

## Virtual.HdaServerExtensions.csx

```csharp
public IEnumerable<HdaItemValue> HdaReadRawAll(HdaTime startTime, HdaTime endTime, int maxValues, bool includeBounds, HdaItem hdaItem)
{
var result = HdaServer.HdaReadRaw(startTime, endTime, maxValues, includeBounds, 
new HdaItem[] { hdaItem });
    var values = new List<HdaItemValue>();

    if (HdaHasMoreData(result))
    {
        values.AddRange(result[0].Values);
        while (HdaReadRawNext(new HdaTime() { AbsoluteTime = result[0].EndTime },
            maxValues, includeBounds, hdaItem, values)) ;
    }
    return values;
}

public bool HdaReadRawNext(HdaTime endTime, int maxValues, bool includeBounds, HdaItem hdaItem, List<HdaItemValue> values)
{
    var startTime = new HdaTime() { AbsoluteTime = values.Last().Timestamp };

    var result = HdaServer.HdaReadRaw(startTime, endTime, maxValues, includeBounds,
        new HdaItemIdentifier[] { hdaItem });
    if (result != null && result.Length > 0)
    {
        values.AddRange(result[0].Values.Skip(1));
        return HdaHasMoreData(result);
    }
    return false;
}

public bool HdaHasMoreData(HdaItemValueCollection[] result)
{
    if (result != null && result.Length > 0)
    {
        if (result[0].ResultID.Name.Name == "S_MOREDATA")
        {
            return true;
        }
    }
    return false;
}

public HdaItemValue[] HdaReadProcessedAll(DateTime startTime, DateTime endTime, int resampleInterval, int maxValues, HdaItem hdaItem)
{
	var values = new List<HdaItemValue>();
	var currentStartTime = startTime;
	var currentEndTime = startTime.AddSeconds(maxValues * resampleInterval);
		
	while (currentStartTime < endTime) {
		if (currentEndTime > endTime) 
			currentEndTime = endTime;

		var result = HdaServer.HdaReadProcessed(
			new HdaTime() { AbsoluteTime = currentStartTime },
			new HdaTime() { AbsoluteTime = currentEndTime },
			resampleInterval, new HdaItem[] { hdaItem }
		);
		
	    if (result != null && result.Length > 0)
			values.AddRange(result[0].Values);
			
		currentStartTime = currentEndTime;
		currentEndTime = currentEndTime.AddSeconds(maxValues * resampleInterval);
	}
	
    return values.ToArray();
}
```

## Virtual.HdaTransitionsStatistics.csx

```csharp
public class HdaTransitionsStatistics
{
    private Func<HdaItemValue, bool> _isInLowState;

    public int Transitions { get; private set; }
    public int LowStateCount { get; private set; }
    public int HighStateCount { get; private set; }
    public TimeSpan LowStateTime { get; private set; }
    public TimeSpan HighStateTime { get; private set; }

    public HdaTransitionsStatistics(Func<HdaItemValue, bool> isInLowState)
    {
        this._isInLowState = isInLowState;
    }

    private void ResetStatistics()
    {
        Transitions = 0;
        LowStateCount = 0;
        HighStateCount = 0;
        LowStateTime = new TimeSpan();
        HighStateTime = new TimeSpan();
    }

    public void Estimate(IEnumerable<HdaItemValue> hdaItemValues, DateTime endTime)
    {
        HdaItemValue lastTransitionValue = null;
        var isCurrentValueInLowState = false;
        var isLastTransitionValueInLowState = false;
        var hasTransition = false;

        ResetStatistics();
        foreach (var currentValue in hdaItemValues)
        {
            if (currentValue.Quality.QualityBits != hdaQualityBits.good &&
                currentValue.Quality.QualityBits != hdaQualityBits.goodLocalOverride)
                continue;

            if (lastTransitionValue == null)
                lastTransitionValue = currentValue;

            isCurrentValueInLowState = _isInLowState(currentValue);
            isLastTransitionValueInLowState = _isInLowState(lastTransitionValue);
            hasTransition = isCurrentValueInLowState ^ isLastTransitionValueInLowState;

            if (hasTransition) {
                if (isLastTransitionValueInLowState) {
                    LowStateTime += (currentValue.Timestamp - lastTransitionValue.Timestamp);
                } else {
                    HighStateTime += (currentValue.Timestamp - lastTransitionValue.Timestamp);
                }

                lastTransitionValue = currentValue;
                Transitions++;
            }

            if (isCurrentValueInLowState) {
                LowStateCount++;
            } else {
                HighStateCount++;
            }
        }

        if (lastTransitionValue != null) {
            if (_isInLowState(lastTransitionValue))  {
                LowStateTime += (endTime - lastTransitionValue.Timestamp.ToUniversalTime());
            } else {
                HighStateTime += (endTime - lastTransitionValue.Timestamp.ToUniversalTime());
            }
        }
    }
}
```

## Virtual.Transitions.Today.csx 

```csharp
@require Virtual.HdaServerExtensions.csx
@require Virtual.HdaTransitionsStatistics.csx

public ItemValue GetVirtualItemValue()
{
	var hdaItem = new HdaItem() { 
			ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE061.PV" 
		};

	var startTime = new HdaTime() {	AbsoluteTime = DateTime.Today.ToUniversalTime() };
	var endTime = new HdaTime()	{ AbsoluteTime = DateTime.Now.ToUniversalTime() };

	var hdaItemValues = HdaReadRawAll(startTime, endTime, 0, false, hdaItem);
	var statistics = new HdaTransitionsStatistics(
		(currentHdaItemValue) => Convert.ToDouble(currentHdaItemValue.Value) < 5000);
	statistics.Estimate(hdaItemValues, endTime.AbsoluteTime);

	return new ItemValue()
	{
		Value = new int[] { 
			statistics.Transitions, 
			statistics.LowStateCount, 
			statistics.HighStateCount, 
			Convert.ToInt32(statistics.LowStateTime.TotalSeconds), 
			Convert.ToInt32(statistics.HighStateTime.TotalSeconds) 
		},
		Quality = new OPCQuality(),
		Timestamp = DateTime.Now,
		TimestampSpecified = true
	};
}
Virtual.Transitions.Yesterday.csx snippet:

@require Virtual.HdaServerExtensions.csx
@require Virtual.HdaTransitionsStatistics.csx

public ItemValue GetVirtualItemValue()
{
	var hdaItem = new HdaItem() { 
			ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE061.PV" 
		};

	var startTime = new HdaTime() { AbsoluteTime = DateTime.Today.AddDays(-1).ToUniversalTime() };
	var endTime = new HdaTime() { AbsoluteTime = DateTime.Today.ToUniversalTime() };

	var hdaItemValues = HdaReadRawAll(startTime, endTime, 0, false, hdaItem);
	var statistics = new HdaTransitionsStatistics(
		(currentHdaItemValue) => Convert.ToDouble(currentHdaItemValue.Value) < 5000);
	statistics.Estimate(hdaItemValues, endTime.AbsoluteTime);

	return new ItemValue()
	{
		Value = new int[] { 
			statistics.Transitions, 
			statistics.LowStateCount, 
			statistics.HighStateCount, 
			Convert.ToInt32(statistics.LowStateTime.TotalSeconds), 
			Convert.ToInt32(statistics.HighStateTime.TotalSeconds) 
		},
		Quality = new OPCQuality(),
		Timestamp = DateTime.Now,
		TimestampSpecified = true
	};
}
```

## Virtual.Transitions.Processed.Today.csx

```csharp
@require Virtual.HdaServerExtensions.csx
@require Virtual.HdaTransitionsStatistics.csx

public ItemValue GetVirtualItemValue()
{
	var hdaItem = new HdaItem() { 
			AggregateID = HdaAggregateID.INTERPOLATIVE,
			ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE061.PV" 
		};

	var startTime = DateTime.Today.ToUniversalTime();
	var endTime = DateTime.Now.ToUniversalTime();

	var hdaItemValues = HdaReadProcessedAll(startTime, endTime, 14240, 100, hdaItem);
	var statistics = new HdaTransitionsStatistics(
		(currentHdaItemValue) => Convert.ToDouble(currentHdaItemValue.Value) < 5000);
	statistics.Estimate(hdaItemValues, endTime);

	return new ItemValue()
	{
		Value = new int[] { 
			statistics.Transitions, 
			statistics.LowStateCount, 
			statistics.HighStateCount, 
			Convert.ToInt32(statistics.LowStateTime.TotalSeconds), 
			Convert.ToInt32(statistics.HighStateTime.TotalSeconds) 
		},
		Quality = new OPCQuality(),
		Timestamp = DateTime.Now,
		TimestampSpecified = true
	};
}
```

## Virtual.Transitions.Processed.Yesterday.csx

```csharp
@require Virtual.HdaServerExtensions.csx
@require Virtual.HdaTransitionsStatistics.csx

public ItemValue GetVirtualItemValue()
{
	var hdaItem = new HdaItem() { 
			AggregateID = HdaAggregateID.INTERPOLATIVE,
			ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE061.PV" 
		};

	var startTime = DateTime.Today.AddDays(-1).ToUniversalTime();
	var endTime = DateTime.Today.ToUniversalTime();

	var hdaItemValues = HdaReadProcessedAll(startTime, endTime, 14240, 100, hdaItem);
	var statistics = new HdaTransitionsStatistics(
		(currentHdaItemValue) => Convert.ToDouble(currentHdaItemValue.Value) < 5000);
	statistics.Estimate(hdaItemValues, endTime);

	return new ItemValue()
	{
		Value = new int[] { 
			statistics.Transitions, 
			statistics.LowStateCount, 
			statistics.HighStateCount, 
			Convert.ToInt32(statistics.LowStateTime.TotalSeconds), 
			Convert.ToInt32(statistics.HighStateTime.TotalSeconds) 
		},
		Quality = new OPCQuality(),
		Timestamp = DateTime.Now,
		TimestampSpecified = true
	};
}
```

