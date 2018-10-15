**Smart OPC XML DA Simulation** plugin provides ability to make items in
the server's address space, which values simulates different kind of
signals.

## Directory Structure

**&lt;InstallDir&gt;** -- This is the base server folder. Here is
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **Simulation** - An **OPC XML DA Simulation** plugin;

>>> **Bin** - Contains binaries of the plugin;

>>> **Config** - Contains configuration files of the plugin;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **Smart OPC XML DA Simulation** plugin configuration is separated in
several **XML** configuration files situated in
**&lt;InstallDir&gt;\\Plugins\\Simulation\\Config** folder. Configuration
attributes of the **Smart OPC XML DA Simulation** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\Simulation\\Config\\Smart.OpcXml.Plugin.Configuration.xml**
file.

*__Example:__*

```xml
<?xml version="1.0"?>
<BasePluginConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used 
  instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Simulation</LoggerName>
  <!-- Value indicating whether plugin supports browse. -->
  <SupportBrowse>true</SupportBrowse>
  <!-- Value indicating whether plugin supports get properties -->
  <SupportGetProperties>true</SupportGetProperties>
  <!-- Value indicating whether plugin supports read. -->
  <SupportRead>true</SupportRead>
  <!-- Value indicating whether plugin supports write. -->
  <SupportWrite>true</SupportWrite>
  <!-- Value indicating whether plugin supports subscribe. -->
  <SupportSubscribe>true</SupportSubscribe>
  <!-- Value indicating whether plugin supports get status. -->
  <SupportGetStatus>true</SupportGetStatus>
  <!-- Plugin module alias. -->
  <Alias>SIMULATION</Alias>
  <!-- Plugin module pathSeparator used for the plugin address space items 
  path and name. -->
  <PathSeparator>.</PathSeparator>
  <!-- Plugin module OriginalPathSeparator used for the plugin address 
  space items path and name. Original path separator is replaced with path 
  separator. -->
  <OriginalPathSeparator>.</OriginalPathSeparator>
  <!-- Minimum requested sampling rate in milliseconds. Value cannot be 
  lower than 1000 ms. -->
  <MinSubscriptionSamplingRate>1000</MinSubscriptionSamplingRate>
  <!-- Default requested sampling rate in milliseconds if such is not 
  specified. Value cannot be lower than 1000 ms. -->
  <DefaultSubscriptionSamplingRate>3000</DefaultSubscriptionSamplingRate>
  <!-- Buffer size of each subscribe request item. Used when 
  EnableBuffering is specified in Subscribe. Cannot be lower than 2. -->
  <MaxSubscriptionItemBufferSize>10</MaxSubscriptionItemBufferSize>
  <!-- Default SubscriptionPingRate in milliseconds if such is not 
  specified in Subscribe. Range [10 000;300 000] ms. -->
  <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
  <!-- The maximum subscribe lists. After reaching that value, the server 
  will not execute subscribes any more until total count of subscribed 
  lists in the server becomes less than that value. MaxSubscriptions cannot 
  be lower than 10. -->
  <MaxSubscriptions>1000</MaxSubscriptions>
  <!-- Maximum allowed number of items per subscribe list.Cannot be lower 
  than 50 -->
  <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
  <!-- Maximum allowed number of items per read list. 0 if no restrictions -->
  <MaxItemsPerRead>0</MaxItemsPerRead>
  <!-- Maximum allowed number of items per write list. 0 if no restrictions -->
  <MaxItemsPerWrite>0</MaxItemsPerWrite>
  <!-- Maximum allowed number of items per get properties list. 0 if no 
  restrictions -->
  <MaxItemsPerGetProperties>0</MaxItemsPerGetProperties>
  <!-- The maximum items returned per browse request. If value is greater 
  than 0, and MaxElementsReturned is 0 or greater than MaxItemsPerBrowse it 
  will be forced to this value. If 0 there is no constraint. -->  
  <MaxItemsPerBrowse>0</MaxItemsPerBrowse>
  <!-- Interval in milliseconds that subscriptions manager should check 
  subscibe request items for new values. DataRefreshInterval cannot be 
  lower than 100ms. -->
  <DataRefreshInterval>1000</DataRefreshInterval>
  <!-- Interval in milliseconds that subscriptions manager should check for 
  and clean expired subscriptions. CleanExpiredSubscriptionsInterval cannot 
  be lower than 1000ms. -->
  <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
  <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be greater 
  than 50000 ms. -->
  <MaxHoldTime>50000</MaxHoldTime>
  <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime cannot 
  be greater than 50000ms. -->
  <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>
  <!-- How many subscriptions should be evaluated by one thread in 
  subscriptions manager. Value cannot be lower than 50. -->
  <EvaluatedSubscriptionsPerThread>400</EvaluatedSubscriptionsPerThread>
  <!-- Maximum items to be read  at once in order to refresh subscriptions 
  data by subscriptions manager. -->
  <MaxRefreshedItemsAtOnce>100</MaxRefreshedItemsAtOnce>
  <!-- Initial capacity of read buffer cache. Specify count of samples. -->
  <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
  <!-- Maximum capacity of read buffer cache. Specify count of samples. -->
  <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>
  <!-- Interval in milliseconds of estimating performance counters. Value 
  cannot be lower than 1000ms. -->
  <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>
  <!-- Interval in milliseconds of estimating read buffer cache counters. 
  Value cannot be lower than 1000ms. -->
  <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>
  <!-- Interval in milliseconds of estimating subscriptions manager 
  counters. Value cannot be lower than 1000ms. -->
  <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>
  <!-- The following limitations are per estimation interval! -->
    <!-- Maximum allowed read requests since last counters snapshot. 0 
    means no limit. -->
  <MaxReadAfterSnapshot>0</MaxReadAfterSnapshot>
  <!-- Maximum allowed write requests since last counters snapshot. 0 means 
  no limit. -->
  <MaxWriteAfterSnapshot>0</MaxWriteAfterSnapshot>
  <!-- Maximum allowed subscribe requests since last counters snapshot. 0 
  means no limit. -->
  <MaxSubscribeAfterSnapshot>0</MaxSubscribeAfterSnapshot>
  <!-- Maximum subscription polled refresh requests since last counters 
  snapshot. 0 means no limit. -->
  <MaxPolledRefreshAfterSnapshot>0</MaxPolledRefreshAfterSnapshot>
  <!-- Maximum allowed browse requests since last counters snapshot. 0 
  means no limit. -->
  <MaxBrowseAfterSnapshot>0</MaxBrowseAfterSnapshot>
  <!-- Maximum allowed get status requests since last counters snapshot. 0 
  means no limit. -->
  <MaxGetStatusAfterSnapshot>0</MaxGetStatusAfterSnapshot>
  <!-- Maximum allowed get properties requests since last counters 
  snapshot. 0 means no limit. -->
  <MaxGetPropertiesAfterSnapshot>0</MaxGetPropertiesAfterSnapshot>
  <!-- Maximum allowed subscription cancels since last counters snapshot. 0 
  means no limit. -->
  <MaxSubscriptionCancelAfterSnapshot>0</MaxSubscriptionCancelAfterSnapshot>
  <!-- Maximum allowed requests since last counters snapshot. 0 means no 
  limit. Must be consistent with other requests type limitations. -->
  <MaxRequestsAfterSnapshot>0</MaxRequestsAfterSnapshot>
 
  <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on first chance exceptions. 
  Use only for debugging purposes.  -->
  <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on unhandled exceptions. Use 
  only for debugging purposes.  -->
  <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->
</BasePluginConfiguration>
```

[Common Configuration Attributes](opc-xml-da-module.md#common-configuration-attributes) of
**Smart OPC XML DA Module** are also valid here.

## Configuring Sumulation Items

Simulation items values are estimated through predefined signal
generator embedded in the plugin. The first thing you have to do when
configuring a simulated item is to define it in the plugin's address
space. The file responsible for describing the pugin's address space is
named "**Smart.OpcXml.AddressSpace.Elements.xml**".

*__Example:__*

```xml
<HierarchicalBrowseElement Name="Demo" ItemPath="" ItemName="Demo" 
IsItem="false" HasChildren="true" >
    <HierarchicalBrowseElement Name="Demo.Sinewave" ItemPath="" 
    ItemName="Demo.Sinewave" IsItem="true" HasChildren="false" />
</HierarchicalBrowseElement>
```

The first element defines a branch node which is used for grouping
elements and its property "**IsItem**" is set to "**false**". Also the
branch has a child, that's why the "**HasChildren**" property is set to
"**true**". The second element inside defines a leaf (item) node
("**IsItem**" is set to "**true**") which is the new virtual item.

*``Remark:`` When configuring a leaf node the "HasChildren" property must
be set to "false". Respectively the leaf node must not have children in
it.*

Items, which exists in the **XML** configuration above, but does not
have properties described, will not be loaded in the server's address
space. That's why we must define the new simulated item properties. Item
properties are described in file with name
"**Smart.OpcXml.AddressSpace.ItemProperties.xml**". Item properties also
defines behavior of the simulated signal.

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Demo.Sinewave</ItemName>
    <ItemPath></ItemPath>
    <dataType>double</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <description>An IEEE double-precision 64-bit floating point sinewave classic signal.</description>
    <highEU>1</highEU>
    <lowEU>-1</lowEU>
    <highIR>1</highIR>
    <lowIR>-1</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
    <maximumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">1</maximumValue>
    <minimumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">-1</minimumValue>
    <valuePrecision>8</valuePrecision>
    <simType>SINEWAVE</simType>
    <param1>60</param1>
  </ItemProperties>
```

The "**simType**" property defines what kind of signal will be
simulated. Possible values are:

-   SINEWAVE

-   SAWTOOTH

-   RECTANGULAR

-   RANDOM

-   CONST

### SINEWAVE signal

The "**simType**" property must be set to "**SINEWAVE**". "**param1**"
property defines period in seconds of the sinewave signal.
"**minimumValue**" and "**maximumValue**" defines respectively minimum
and maximum of the sinewave signal. "**valuePrecision**" defines the
number of digits after decimal separator.

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Signal.Sinewave.Classic</ItemName>
    <ItemPath></ItemPath>
    <dataType>double</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <description>An IEEE double-precision 64-bit floating point sinewave classic signal.</description>
    <highEU>1</highEU>
    <lowEU>-1</lowEU>
    <highIR>1</highIR>
    <lowIR>-1</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
    <maximumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">1</maximumValue>
    <minimumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">-1</minimumValue>
    <valuePrecision>8</valuePrecision>
    <simType>SINEWAVE</simType>
    <param1>60</param1>
  </ItemProperties>
```

### SAWTOOTH signal

The "**simType**" property must be set to "**SAWTOOTH**". "**param1**"
property defines period in seconds of the sawtooth signal.
"**minimumValue**" and "**maximumValue**" defines respectively minimum
and maximum of the sawtooth signal. "**valuePrecision**" defines the
number of digits after decimal separator.

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Signal.Sawtooth.Classic</ItemName>
    <ItemPath></ItemPath>
    <dataType>double</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <description>An IEEE double-precision 64-bit floating point classic sawtooth signal.</description>
    <highEU>1</highEU>
    <lowEU>-1</lowEU>
    <highIR>1</highIR>
    <lowIR>-1</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
    <maximumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">1</maximumValue>
    <minimumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">-1</minimumValue>
    <valuePrecision>8</valuePrecision>
    <simType>SAWTOOTH</simType>
    <param1>30</param1>
</ItemProperties>
```


### RECTANGULAR signal

The "**simType**" property must be set to "**RECTANGULAR**".
"**param1**" property defines highstate period in seconds of the signal.
"**param2**" property defines lowstate period in seconds of the signal.
"**minimumValue**" and "**maximumValue**" defines respectively highstate
and lowstate of the rectangular signal.

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Signal.Rectangular.Classic</ItemName>
    <ItemPath></ItemPath>
    <dataType>double</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <description>An IEEE double-precision 64-bit floating point classic rectangular signal.</description>
    <highEU>1</highEU>
    <lowEU>-1</lowEU>
    <highIR>1</highIR>
    <lowIR>-1</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
    <maximumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">1</maximumValue>
    <minimumValue xsi:type="xsd:double" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">-1</minimumValue>
    <valuePrecision>8</valuePrecision>
    <simType>RECTANGULAR</simType>
    <param1>30</param1>
    <param2>30</param2>
</ItemProperties>
```

### RANDOM signal

The "**simType**" property must be set to "**RANDOM**".
"**minimumValue**" and "**maximumValue**" defines respectively minimum
and maximum of the random generated signal.

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Random.UnsignedLong</ItemName>
    <ItemPath></ItemPath>
    <dataType>unsignedLong</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <description>A 64-bit unsigned integer value.</description>
    <highEU>2147483647</highEU>
    <lowEU>0</lowEU>
    <highIR>18446744073709551614</highIR>
    <lowIR>0</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:unsignedLong" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
    <maximumValue xsi:type="xsd:unsignedLong" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">2147483647</maximumValue>
    <minimumValue xsi:type="xsd:unsignedLong" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</minimumValue>
    <simType>RANDOM</simType>
  </ItemProperties>
```

### CONST signal

The "**simType**" property must be set to "**CONST**".

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Const.UnsignedShort</ItemName>
    <ItemPath></ItemPath>
    <dataType>unsignedShort</dataType>
    <accessRights>readWritable</accessRights>
    <scanRate>1000</scanRate>
    <euType>noEnum</euType>
    <description>A 16-bit unsigned integer value.</description>
<!—
<highEU>65535</highEU>
<lowEU>0</lowEU>
-->
    <highIR>65535</highIR>
    <lowIR>0</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:unsignedShort" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">65535</value>
    <maximumValue xsi:type="xsd:unsignedShort" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">65535</maximumValue>
    <minimumValue xsi:type="xsd:unsignedShort" xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</minimumValue>
    <simType>CONST</simType>
  </ItemProperties>
```


For more information about "**ItemProperties**" element you can see in
appendices
[here](opc-xml-da-address-space-item-properties.md).