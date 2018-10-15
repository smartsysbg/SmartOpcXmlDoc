**Smart OPC XML DA Virtualize** plugin provides ability to make virtual
items in the server's address space, which values are calculated through
scripts written in **C\#**.

## Directory Structure

**&lt;InstallDir&gt;** - This is the base server folder. Here is
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **Virtualize** - An **OPC XML DA Virtualize** plugin;

>>> **Bin** - Contains binaries of the plugin;

>>>> **AddIns** - Contains plugin module addins;

>>>>> **Slot0** - Slot 0 of the Virtualize Addin;

>>>>> **Slot1** - Slot 1 of the Virtualize Addin;

>>> **Config** - Contains configuration files of the plugin;

>>>> **Scripts** - Contains **C\#** scripts (**\*.csx**) of the virtual
items;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **Smart OPC XML DA Virtualize** plugin configuration is separated in
several **XML** configuration files situated in
**&lt;InstallDir&gt;\\Plugins\\Virtualize\\Config** folder. Configuration
attributes of the **Smart OPC XML DA Virtualize** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\Virtualize\\Config\\Smart.OpcXml.Plugin.Configuration.xml**
file.

*__Example:__*

```xml
<?xml version="1.0"?>
<VirtualizePluginConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Virtualize</LoggerName>
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
  <Alias>VIRTUALIZE</Alias>
  <!-- Plugin module pathSeparator used for the plugin address space items path and name. -->
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
  will not execute subscribes any more until
  total count of subscribed lists in the server becomes less than that 
  value. MaxSubscriptions cannot be lower than 10. -->
  <MaxSubscriptions>1000</MaxSubscriptions>
  <!-- Maximum allowed number of items per subscribe list.Cannot be lower 
  than 50 -->
  <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
  <!-- Maximum allowed number of items per read list. 0 if no restrictions -->
  <MaxItemsPerRead>0</MaxItemsPerRead>
  <!-- Maximum allowed number of items per write list. 0 if no restrictions -->
  <MaxItemsPerWrite>0</MaxItemsPerWrite>
  <!-- Maximum allowed number of items per get properties list. 0 if no restrictions -->
  <MaxItemsPerGetProperties>0</MaxItemsPerGetProperties>
  <!-- The maximum items returned per browse request. If value is greater 
  than 0, and MaxElementsReturned is 0 or greater than MaxItemsPerBrowse it 
  will be forced to this value. If 0 there is no constraint. -->
  <MaxItemsPerBrowse>0</MaxItemsPerBrowse>
  <!-- Interval in milliseconds that subscriptions manager should check 
  subscribe request items for new values. DataRefreshInterval cannot be 
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
  <!-- Maximum allowed read requests since last counters snapshot. 0 means 
  no limit. -->
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
  <!--<DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>-->

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on unhandled exceptions. Use 
  only for debugging purposes.  -->
  <!--<DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>-->

  <!-- Interval in milliseconds to wait before to start the new add in 
  process. Range [10000 - 120000]ms.-->
  <!-- If TcpClientChannelSocketCacheTimeout parameter in 
  Smart.OpcXml.Service.Configuration.xml configuration file 
  is not set or is 5000 ms, then this parameter should be 30000ms. If 
  TcpClientChannelSocketCacheTimeout is 30000ms., this parameter 
  must be set at the maximum of 120000ms. This is important if you choose 
  to use remoting proxy services OpcXmlDaRem.asmx and OpcXmlHdaRem.asmx.
  But if you use only OpcXmlDa.asmx and OpcXmlHda.asmx web service, which 
  do not use remoting proxies, then you may set this 
  parameter to 10000ms -->
  <AddInProcessRestartWaitTime>30000</AddInProcessRestartWaitTime>
  <!-- Interval in milliseconds of checking OpcServer modules connection 
  state. Value cannot be lower than 3000 ms. -->
  <CheckAddInStateInterval>3000</CheckAddInStateInterval>
  <!--  Memory threshold in mega bytes after that the addIn process will be 
  recycled. 0 means no limit.-->
  <ProcessMemoryThreshold>1024</ProcessMemoryThreshold>
</VirtualizePluginConfiguration>
```

[Common Configuration Attributes](opc-xml-da-module.md#common-configuration-attributes) of
**Smart OPC XML DA Module** are also valid here. We will describe here
additional configuration attributes only.

\[**AddInProcessRestartWaitTime**\]

> Interval in milliseconds to wait before to start the new add in process.
Range \[**10000** - **120000**\] ms.

>  *``Remark:`` If **TcpClientChannelSocketCacheTimeout** parameter in
**Smart.OpcXml.Service.Configuration.xml** configuration file is not set
or is **5** seconds, then this parameter should be **30000ms**. If
**TcpClientChannelSocketCacheTimeout** is **30** seconds, this parameter
must be set at the maximum of **120000ms**. This is important if you
choose to use remoting proxy services **OpcXmlDaRem.asmx** and
**OpcXmlHdaRem.asmx**. But if you use only **OpcXmlDa.asmx** and
**OpcXmlHda.asmx** web service, which do not use remoting proxies, then
you may set this parameter to **10000ms**.*

\[**CheckAddInStateInterval**\]

> Interval in milliseconds for checking **AddIn's** state. Value cannot be
lower than 3000 ms.

\[**ProcessMemoryThreshold**\]

> Memory threshold in mega bytes after that the addIn process will be
recycled. 0 means no limit.

## AddIn Slots

The **Virtualize** plugin raises two separate addin process using
managed add-in framework. Because of technology constraint it is not
possible to raise two addin processes from the same place. That's the
reason why we use slots for each addin process. The slots are situated
in

**&lt;InstallDir&gt;** -- This is the base server folder. Here is situated
the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **Virtualize** - An **OPC XML DA Virtualize** plugin module;

>>> **Bin** - Contains binaries of the plugin module;

>>> **AddIns** - Contains plugin module addins;

>>>> **Slot0** - Slot 0 of the Virtualize Addin;

>>>> **Slot1** - Slot 1 of the Virtualize Addin;

The plugin uses the addin with the largest allocated memory to execute
the scripts. When an AddIn's allocated memory reaches the threshold
configured by the "**ProcessMemoryThreshold**" property in the
configuration file, the calculations are transferred to the second AddIn
and the first one is recycled.

## Configuring Virtual Items

Virtual items values are estimated through scripts written in **C\#**,
situated in script files which are located in the "**Scripts**" folder.
The recommended extension used for script files is "**.csx**". The
recommended rule for constructing the script file name is "**\[Virtual
item name\].csx**". The first thing you have to do when configuring a
virtual item is to define it in the plugin's address space. The file
responsible for describing the pugin's address space is named
"**Smart.OpcXml.AddressSpace.Elements.xml**".

*__Example:__*

```xml
<HierarchicalBrowseElement Name="Virtual" ItemPath="" ItemName="Virtual" 
IsItem="false" HasChildren="true" >
    <HierarchicalBrowseElement Name="Virtual.DemoItem" ItemPath="" 
    ItemName="Virtual.DemoItem" IsItem="true" HasChildren="false" />
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
space. That's why we must define the new virtual item properties. Item
properties are described in file with name
"**Smart.OpcXml.AddressSpace.ItemProperties.xml**".

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Virtual.DemoItem</ItemName>
    <ItemPath></ItemPath>
    <dataType>unsignedInt</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <engineeringUnits></engineeringUnits>
    <description>Calculated virtual item.</description>
<!--
    <highEU>4294967290</highEU>
    <lowEU>0</lowEU>
    <highIR>4294967290</highIR>
    <lowIR>0</lowIR>
    <closeLabel></closeLabel>
    <openLabel></openLabel>
-->
    <timeZone>120</timeZone>
    <value xsi:type="xsd:unsignedInt" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
<!--
    <maximumValue xsi:type="xsd:unsignedInt" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">4294967290</maximumValue>
    <minimumValue xsi:type="xsd:unsignedInt" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</minimumValue>
-->
    <virtualItem>true</virtualItem>
    <virtualScriptPath>Virtual.DemoItem.csx</virtualScriptPath>
  </ItemProperties>
```

Commented tags are optional. You can uncomment it and write the values
you want according to the **OPC XML DA Specification**. The
**&lt;virtualItem&gt;true&lt;/virtualItem&gt;** is mandatory. It defines that
this is virtual item and its value will be provided via script located
in **&lt;virtualScriptPath&gt;Virtual.DemoItem.csx&lt;/virtualScriptPath&gt;.**
Virtual script path is relative path starting from "**\[Plugin
folder\]\\Config\\Scripts\\**" pointing to where the script is located.
Create new file in "**\[Plugin folder\]\\Config\\Scripts**" named
"**Virtual.DemoItem.csx**". Open the file with a text editor and write
the following snippet:

```csharp
public ItemValue GetVirtualItemValue()
{
    OPCError[] err = null;
    ReplyItemList result = null;
    var options = new RequestOptions() { ReturnItemTime = true };
    var itemList = new ReadRequestItemList()
    {
Items = new ReadRequestItem[] { new ReadRequestItem() { ItemName = "SIMULATION.Random.UnsignedInt" } }
    };
    DaServer.Read(options, itemList, out result, out err);
    return result.Items[0];
}
```
Always you must write a function "**public ItemValue GetVirtualItemValue
() {}**". It must return "**ItemValue**" type with filled appropriate
data. When the function is called you have access to 3 system
properties:

-   **public IOpcXmlDa DaServer { get; set; }** - An interface to the
    **OPC XML Data Access** part of the **Smart OPC XML Server**;

-   **public IOpcXmlHda HdaServer { get; set; }** - An interface to the
    **OPC XML History Data Access** part of the **Smart OPC XML
    Server;**

-   **public ItemValue Item { get; set; }** - Item value filled with
    appropriate item name and path of the requested item.

Via "**DaServer**" variable you have full access to the 8 actions as
specified in **OPC XML DA** Specification (**Browse**, **Read**,
**Write**, **Subscribe**, **SubscriptionPolledRefresh**,
**SubscriptionCancel**, **GetStatus** and **GetProperties**). Via
**HdaServer** variable you have full access to the 6 actions as
specified in **OPC History Data Access** specification (**HdaBrowse**,
**HdaGetAggregates**, **HdaGetStatus**, **HdaReadAtTime**,
**HdaReadProcessed** and **HdaReadRaw**). **HdaReadAtTime** is not
mandatory and thus is not supported by some **OPC HDA** servers.

You can include a script file into other by using "**@require**"
directive.

*__Example:__*

```
@require somescriptfile.csx
...
```

The "**@require**" directive is recommended to be at the beginning of
the script file. Thus using "**@require**" you can write reusable
snippets of code which you can import into other scripts for estimating
values of various virtual items.

A short reference to the **OPC XML DA** interface, methods and used
typed you can find in appendices
[here](opc-xml-da-interface-short-reference.md).

## More Snippets

### Returning Status Info From GetStatus Action Into DA Virtual Item

The following snippet illustrates how we can return the **StatusInfo**
of the server obtained through **GetStatus** command of the
**DaServer**. It is very important to understand that you must always
return **ItemValue** with filled **Value**, **Quality** and
**Timestamp** properties. **TimestampSpecified** must be always
"**true**". **ResultID** is not required, but you can use it to return
an error. Remember that if error is specific not accoriding to **OPC XML
DA** specification, you must provide custom namespace of the error in
order to stay compliant with the specification (e.g. **ResultID = new
XmlQualifiedName("MY\_ERROR","http://my.company.com");** ).

```csharp
public ItemValue GetVirtualItemValue()
    {
        ServerStatus status = null;
        DaServer.GetStatus(null, null, out status);
        return new ItemValue()
        {
            Value = status.StatusInfo,
            Quality = new OPCQuality(),
            Timestamp = DateTime.Now,
            TimestampSpecified = true,
            ResultID = null
        };
    }
```

### Extracting Value Using History Data Access Feature

```csharp
public ItemValue GetVirtualItemValue()
    {
        HdaTime startTime = new HdaTime() {
           IsRelative = true,
           BaseTime = HdaRelativeTime.Now,
           Offsets = new HdaTimeOffset[] { new HdaTimeOffset() { Type = HdaRelativeTime.Day, Value = -1 } }
        };
        HdaTime endTime = new HdaTime(){
            IsRelative = true,
            BaseTime = HdaRelativeTime.Now
        };
        HdaItemValueCollection[] result = 
            HdaServer.HdaReadProcessed(startTime, 
                endTime, 0, new HdaItem[] { 
                    new HdaItem() { 
                        ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE.PV",  
                        AggregateID = HdaAggregateID.AVERAGE
                    } 
                });
        return new ItemValue() {
            Value = result[0].Values[0].Value,
            Quality = new OPCQuality(),
            Timestamp = DateTime.Now,
            TimestampSpecified = true,
            ResultID = result[0].ResultID.Name.Name != "S_OK" ? result[0].ResultID.Name : null
        };
}
```

*``Remark:`` In this sample is not provided logic how to translate
**HdaQuality** to **OPC XML DA Quality**.*

More snippets you can find in appendices [here](opc-xml-da-virtualize-plugin-snippets.md).