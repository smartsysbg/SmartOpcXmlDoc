**Smart OPC XML HDA Virtualize** plugin provides ability to make virtual
items in the server's address space, which values are calculated through
scripts written in **C\#**.

## Directory Structure

**&lt;InstallDir&gt;** - This is the base server folder. Here is
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **HdaVirtualize** - An **OPC XML HDA Virtualize** plugin;

>>> **Bin** - Contains binaries of the plugin;

>>>> **AddIns** - Contains plugin module addins;

>>>>> **Slot0** - Slot 0 of the HdaVirtualize Addin;

>>>>> **Slot1** - Slot 1 of the HdaVirtualize Addin;

>>> **Config** - Contains configuration files of the plugin;

>>>> **Scripts** - Contains **C\#** scripts (**\*.csx**) of the virtual
items;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **Smart OPC XML HDA Virtualize** plugin configuration is separated
in several **XML** configuration files situated in
**&lt;InstallDir&gt;\\HdaPlugins\\HdaVirtualize\\Config** folder.
Configuration attributes of the **Smart OPC XML HDA Virtualize** plugin
are located in
**&lt;InstallDir&gt;\\Plugins\\HdaVirtualize\\Config\\Smart.OpcXml.Plugin.Configuration.xml**
file.

__Example:__

```xml
<?xml version="1.0"?>
<HdaVirtualizePluginConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Hda.HdaVirtualize</LoggerName>

  <!-- Value indicating whether plugin supports HdaReadRaw. -->
  <SupportHdaReadRaw>true</SupportHdaReadRaw>
  <!-- Value indicating whether plugin supports HdaReadProcessed. -->
  <SupportHdaReadProcessed>true</SupportHdaReadProcessed>
  <!-- Value indicating whether plugin supports HdaReadAtTime. -->
  <SupportHdaReadAtTime>true</SupportHdaReadAtTime>
  <!-- Value indicating whether plugin supports HdaGetAggregates. -->
  <SupportHdaGetAggregates>true</SupportHdaGetAggregates>
  <!-- Value indicating whether plugin supports HdaGetStatus. -->
  <SupportHdaGetStatus>true</SupportHdaGetStatus>
  <!-- Value indicating whether plugin supports HdaBrowse. -->
  <SupportHdaBrowse>true</SupportHdaBrowse>

  <!-- Plugin module alias. -->
  <Alias>VIRTUALIZE</Alias>
  <!-- Plugin module pathSeparator used for the plugin address space items path and name. -->
  <PathSeparator>.</PathSeparator>
  <!-- Plugin module OriginalPathSeparator used for the plugin address space 
  items path and name. Original path separator is replaced with path separator. -->
  <OriginalPathSeparator>.</OriginalPathSeparator>

  <!-- Maximum available items to read at once via HdaReadAtTime. 0 means no restriction. -->
  <MaxItemsPerHdaReadAtTime>0</MaxItemsPerHdaReadAtTime>
  <!-- Maximum available items to read at once via HdaReadProcessed. 0 means no restriction. -->
  <MaxItemsPerHdaReadProcessed>0</MaxItemsPerHdaReadProcessed>
  <!-- Maximum available items to read at once via HdaReadRaw. 0 means no restriction. -->
  <MaxItemsPerHdaReadRaw>0</MaxItemsPerHdaReadRaw>

  <!-- Interval in milliseconds of estimating HDA performance counters. Value 
  cannot be lower than 1000ms. -->
  <HdaPerformanceCountersEstimationInterval>60000</HdaPerformanceCountersEstimationInterval>

  <!-- Max number of HdaReadRaw requests since last counters snapshot  after that 
  the server will response with E_REJECTED on HdaReadRaw requests.  0 means no 
  limitations. -->
  <MaxHdaReadRawAfterSnapshot>0</MaxHdaReadRawAfterSnapshot>
  <!--Max number of HdaReadProcessed requests since last counters snapshot after 
  that the server will response with E_REJECTED on HdaReadProcessed requests. 
  0 means no limitations. -->
  <MaxHdaReadProcessedAfterSnapshot>0</MaxHdaReadProcessedAfterSnapshot>
  <!-- Max number of HdaReatAtTime requests since last counters snapshot after 
  that the server will response with E_REJECTED on HdaReadAtTime requests. 
  0 means no limitations. -->
  <MaxHdaReadAtTimeAfterSnapshot>0</MaxHdaReadAtTimeAfterSnapshot>
  <!-- Max number of HdaGetAggregates requests since last counters snapshot after 
  that the server will response with E_REJECTED on HdaGetAggregates requests. 
  0 means no limitations. -->
  <MaxHdaGetAggregatesAfterSnapshot>0</MaxHdaGetAggregatesAfterSnapshot>
  <!-- Max number of HdaGetStatus requests since last counters snapshot after 
  that the server will response with E_REJECTED on HdaGetStatus requests. 
  0 means no limitations. -->
  <MaxHdaGetStatusAfterSnapshot>0</MaxHdaGetStatusAfterSnapshot>
  <!-- Max number of HdaBrowse requests since last counters snapshot after that 
  the server will response with E_REJECTED on HdaBrowse requests. 
  0 means no limitations. -->
  <MaxHdaBrowseAfterSnapshot>0</MaxHdaBrowseAfterSnapshot>
  <!-- Max number of requests since last counters snapshot after that the server 
  will response with E_REJECTED on all requests. 0 means no limitations. -->
  <MaxHdaRequestsAfterSnapshot>0</MaxHdaRequestsAfterSnapshot>

  <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be attached 
  to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on first chance exceptions. Use only 
  for debugging purposes.  -->
  <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be attached to 
  the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on unhandled exceptions. Use only 
  for debugging purposes.  -->
  <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->

  <!-- Interval in milliseconds to wait before to start the new add in process. 
  Range [10000 - 120000]ms.-->
  <!-- If TcpClientChannelSocketCacheTimeout parameter in 
  Smart.OpcXml.Service.Configuration.xml configuration file 
  is not set or is 5000 ms, then this parameter should be 30000ms. If 
  TcpClientChannelSocketCacheTimeout is 30000ms., this parameter 
  must be set at the maximum of 120000ms. This is important if you choose to use 
  remoting proxy services OpcXmlDaRem.asmx and OpcXmlHdaRem.asmx.
  But if you use only OpcXmlDa.asmx and OpcXmlHda.asmx web service, which do not 
  use remoting proxies, then you may set this parameter to 10000ms -->
  <AddInProcessRestartWaitTime>30000</AddInProcessRestartWaitTime>
  <!-- Interval in milliseconds of checking AddIn state. Value cannot be lower than 3000 ms. -->
  <CheckAddInStateInterval>3000</CheckAddInStateInterval>
  <!--  Memory threshold in mega bytes after that the addIn process will be 
  recycled. 0 means no limit.-->
  <ProcessMemoryThreshold>1024</ProcessMemoryThreshold>
</HdaVirtualizePluginConfiguration>
```

[Common Configuration Attributes](opc-xml-hda-module.md#common-configuration-attributes) of
**Smart OPC XML HDA Module** are also valid here. We will describe here
additional configuration attributes only.

\[**AddInProcessRestartWaitTime**\]

> Interval in milliseconds to wait before to start the new add in process.
Range \[**10000** - **120000**\] ms.

*``Remark:`` If **TcpClientChannelSocketCacheTimeout** parameter in
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

##AddIn Slots

The **HdaVirtualize** plugin raises two separate addin process using
managed add-in framework. Because of technology constraint it is not
possible to raise two addin processes from the same place. That's the
reason why we use slots for each addin process. The are slots situated
in

**&lt;InstallDir&gt;** - This is the base server folder. Here is situated
the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **HdaVirtualize** - An **OPC XML HDA Virtualize** plugin module;

>>> **Bin** - Contains binaries of the plugin module;

>>>> **AddIns** - Contains plugin module addins;

>>>>> **Slot0** - Slot 0 of the HdaVirtualize Addin;

>>>>> **Slot1** - Slot 1 of the HdaVirtualize Addin;

The plugin uses the addin with the largest allocated memory to execute
the scripts. When an AddIn's allocated memory reaches the threshold
configured by the "**ProcessMemoryThreshold"** property in the
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

__Example:__

```xml
<HierarchicalHdaBrowseElement Name="Virtual" ItemPath="" ItemName="Virtual" IsItem="false" 
HasChildren="true" >
    <HierarchicalHdaBrowseElement Name="DemoItem" ItemPath="" ItemName="Virtual.DemoItem" 
    IsItem="true" HasChildren="false" VirtualScriptPath="Virtual.DemoItem.csx"/>
</HierarchicalHdaBrowseElement>
```

The first element defines a branch node which is used for grouping
elements and its property "**IsItem**" is set to "**false**". Also the
branch has a child, that's why the "**HasChildren**" property is set to
"**true**". The second element inside defines a leaf (item) node
("**IsItem**" is set to "**true**") which is the new virtual item.

*``Remark:`` When configuring a leaf node the "HasChildren" property must
be set to "false". Respectively the leaf node must not have children in
it.*

Virtual item value will be provided via script located in
**VirtualScriptPath ="Virtual.DemoItem.csx"**. Virtual script path is
relative path starting from "**\[Plugin folder\]\\Config\\Scripts\\**"
pointing to where the script is located. Create new file in "**\[Plugin
folder\]\\Config\\Scripts**" named "**Virtual.DemoItem.csx**". Open the
file with a text editor and write the following snippet:

```csharp
public HdaItemValueCollection VirtualHdaReadRaw() {
        var itemId = new HdaItemIdentifier(){
            ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE.PV"
        };
        var result = HdaServer.HdaReadRaw(StartTime, 
                                          EndTime, 
                                          MaxValues, 
                                          IncludeBounds, 
                                          new HdaItemIdentifier[] { itemId });
        return result[0];
    }

    public HdaItemValueCollection VirtualHdaReadProcessed() {
        var itemId = new HdaItem() {
            ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE.PV",
            AggregateID = Item.AggregateID
        };
        var result = HdaServer.HdaReadProcessed(StartTime, 
                                                EndTime, 
                                                ResampleInterval, 
                                                new HdaItem[] { itemId });
        return result[0];
    }

    public HdaAggregate[] VirtualHdaGetAggreagates()
    {
        return HdaServer.HdaGetAggregates(
            new HdaItemIdentifier() {
                ItemName = "OPC.SWP-EPKS-410./ASSETS/01/SINEWAVE.PV"
            });
   }
```

Always you must write 3 functions:

```csharp
public HdaItemValueCollection VirtualHdaReadRaw(){}

public HdaItemValueCollection VirtualHdaReadProcessed(){}

public HdaAggregate[] VirtualHdaGetAggreagates(){}
```

These 3 functions are mandatory regarding the classic **OPC History Data
Access** specification. When a given function is called you have access
to 9 system properties:

-   `public IOpcXmlDa DaServer { get; set; }` - An interface to the
    **OPC XML Data Access** part of the **Smart OPC XML Server**;

-   `public IOpcXmlHda HdaServer { get; set; }` - An interface to the
    **OPC XML History Data Access** part of the **Smart OPC XML
    Server**;

-   `public HdaItem Item { get; set; }` - Item filled with
    appropriate item name and path of the requested item (filled only
    when **VirtualHdaReadProcessed** is called);

-   `public HdaTime StartTime { get; set; }` - start time of the
    history data access interval (filled only when **VirtualHdaReadRaw**
    or **VirtualHdaReadProcessed** are called);

-   `public HdaTime EndTime { get; set; }` - end time of the history
    data access interval (filled only when **VirtualHdaReadRaw** or
    **VirtualHdaReadProcessed** are called);

-   `public int MaxValues { get; set; }` - Maximum values to return
    (0 -- default). Server returns an error if you specify value greater
    than is supported by **OPC HDA** server (filled only when
    **VirtualHdaReadRaw** is called);

-   `public bool IncludeBounds { get; set; }` - Specifies if to
    include bounds Start-End times of the requested history data access
    interval (filled only when **VirtualHdaReadRaw** is called);

-   `public decimal ResampleInterval { get; set; }` - resample
    interval in seconds (filled only when **VirtualHdaReadProcessed** is
    called);

-   `public HdaItemIdentifier ItemIdentifier { get; set; }` - Item
    filled with appropriate item name and path of the requested item
    (filled only when **VirtualHdaReadProcessed** or
    **VirtualHdaGetAggregates** are called).

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

__Example:__

```csharp
@require somescriptfile.csx
...
```

The "**@require**" directive is recommended to be at the beginning of
the script file. Thus using "**@require**" you can write reusable
snippets of code which you can import into other scripts for estimating
values of various virtual items.

A short reference to the **OPC XML HDA** interface, methods and used
typed you can find in appendices
[here](opc-xml-hda-interface-short-reference.md).