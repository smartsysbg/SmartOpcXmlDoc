**Smart OPC XML Server** provides two basic data access modules -
**Smart OPC XML Data Access** and **Smart OPC XML Historical Data
Access**. **Smart OPC XML DA Module** is one of the basic parts of the
entire **Smart OPC XML Server**. Configuration of the **Smart OPC XML
DA** module is separated in several **XML** configuration files situated
in **&lt;InstallDir&gt;\\Config** folder.

## Common Configuration Attributes

**Smart OPC XML DA Module** provides an **API** for developing new **OPC
XML Data Access** plugins. So there are configuration parameters which
are common for the module and all of this type plugins. Of course they
are not mandatory and developer may override the functionality and thus
to bypass them.

\[**LoggerName**\]

> Provides the **NLog** logger name. If empty or omitted null logger will
be used instead.

\[**MinSubscriptionSamplingRate**\]

> Minimum requested sampling rate in milliseconds. Value cannot be lower
than 1000ms.

\[**DefaultSubscriptionSamplingRate**\]

> Default requested sampling rate in milliseconds if such is not
specified. Value cannot be lower than 1000ms.

\[**MaxSubscriptionItemBufferSize**\]

> Buffer size of each subscribe request item. Used when
**EnableBuffering** is specified in **Subscribe** (refer to the **OPC
XML DA** specification). Value cannot be lower than 2.

\[**DefaultSubscriptionPingRate**\]

> Default **SubscriptionPingRate** in milliseconds if such is not
specified in **Subscribe** (refer to the **OPC XML DA** specification).
Value cannot be lower than 10000ms.

\[**MaxSubscribedItems**\]

> The maximum subscribed items. After reaching that value, the server will
not execute subscribes any more until total count of subscribed items in
the server becomes less than that value. Value cannot be lower than 0. 0
means no restrictions.

\[**MaxSubscriptions**\]

> The maximum subscribe lists. After reaching that value, the server will
not execute subscribes any more until total count of subscribed lists in
the server becomes less than that value. Value cannot be lower than 10.

\[**MaxItemsPerSubscription**\]

> Maximum allowed number of items per subscribe list. Cannot be lower than 50.

\[**MaxItemsPerRead**\]

> Maximum allowed number of items per read list. 0 if no restrictions.

\[**MaxItemsPerWrite**\]

> Maximum allowed number of items per write list. 0 if no restrictions.

\[**MaxItemsPerGetProperties**\]

> Maximum allowed number of items per get properties list. 0 if no
restrictions.

\[**MaxItemsPerBrowse**\]

> The maximum items returned per browse request. If value is greater than
0, and **MaxElementsReturned** is 0 or greater than
**MaxItemsPerBrowse** it will be forced to this value. If 0 there is no
constraint.

\[**DataRefreshInterval**\]

> Interval in milliseconds that subscriptions manager should check
subscibe request items for new values. Value cannot be lower than 100ms.

\[**CleanExpiredSubscriptionsInterval**\]

> Interval in milliseconds that subscriptions manager should check for and
clean expired subscriptions. Value cannot be lower than 1000ms.

\[**MaxHoldTime**\]

> The maximum **HoldTime** in milliseconds. Value cannot be greater than
50000ms.

\[**MaxHoldAndWaitTime**\]

> Maximum **HoldTime+WaitTime** in milliseconds. Value cannot be greater
than 50000ms.

\[**EvaluatedSubscriptionsPerThread**\]

> How many subscriptions should be evaluated by one thread in
subscriptions manager. Value cannot be lower than 50

\[**MaxRefreshedItemsAtOnce**\]

> Maximum items to be read at once in order to refresh subscriptions data
by subscriptions manager.

\[**ReadBufferCacheInitialCapacity**\]

> Initial capacity of read buffer cache. Specify count of samples.

\[**ReadBufferCacheMaxSize**\]

> Maximum capacity of read buffer cache. Specify count of samples.

\[**PerformanceCountersEstimationInterval**\]

> Interval in milliseconds of estimating performance counters. Value
cannot be lower than 1000ms.

\[**ReadBufferCacheCountersEstimationInterval**\]

> Interval in milliseconds of estimating read buffer cache counters. Value
cannot be lower than 1000ms.

\[**SubscriptionsManagerCountersEstimationInterval**\]

> Interval in milliseconds of estimating subscriptions manager counters.
Value cannot be lower than 1000ms.

\[**MaxReadAfterSnapshot**\]

> Max allowed read requests since last counters snapshot (i.e. max number
of requests are per specified subscriptions manager counters estimation
interval). 0 means no limit. **E\_REJECTED** is thrown if the limit is
reached.

\[**MaxWriteAfterSnapshot**\]

> Max allowed write requests since last counters snapshot (i.e. max number
of requests are per specified subscriptions manager counters estimation
interval). 0 means no limit. **E\_REJECTED** is thrown if the limit is
reached.

\[**MaxSubscribeAfterSnapshot**\]

> Max allowed subscribe requests since last counters snapshot (i.e. max
number of requests are per specified subscriptions manager counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxPolledRefreshAfterSnapshot**\]

> Max allowed subscription polled refresh requests since last counters
snapshot (i.e. max number of requests are per specified subscriptions
manager counters estimation interval). 0 means no limit. **E\_REJECTED**
is thrown if the limit is reached.

\[**MaxBrowseAfterSnapshot**\]

> Max allowed browse requests since last counters snapshot (i.e. max
number of requests are per specified subscriptions manager counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxGetStatusAfterSnapshot**\]

> Max allowed get status requests since last counters snapshot (i.e. max
number of requests are per specified subscriptions manager counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxGetPropertiesAfterSnapshot** Attribute

> Max allowed get properties requests since last counters snapshot (i.e.
max number of requests are per specified subscriptions manager counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxSubscriptionCancelAfterSnapshot**\]

> Max allowed subscription cancel requests since last counters snapshot
(i.e. max number of requests are per specified subscriptions manager
counters estimation interval). 0 means no limit. **E\_REJECTED** is
thrown if the limit is reached.

\[**MaxRequestsAfterSnapshot**\]

> Max allowed requests since last counters snapshot (i.e. max number of
requests are per specified subscriptions manager counters estimation
interval). 0 means no limit. Must be consistent with other requests type
limitations. **E\_REJECTED** is thrown if the limit is reached.

\[**DebugTraceFirstChanceExceptions**\]

> If you set "**DebugTraceFirstChanceExceptions"** to "**true**", then an
event handler will be attached to the application domain first chance
exceptions handler and all exceptions will be traced to the log.

\[**DebugTraceUnhandledExceptions**\]

> If you set "**DebugTraceUnhandledExceptions"** to "**true**", then an
event handler will be attached to the application domain unhandled
exceptions handler and all unhandled exceptions will be traced to the
log. Also in the log will be traced if the exception is terminating or
not.

> *``Remark:`` Be careful when use "**DebugTraceFirstChanceExceptions"**
and "**DebugTraceUnhandledExceptions"** options, the log files can grow
dramatically if you leave them turned on. Use only for debugging
purposes.*

## Configuration Attributes

Configuration attributes of the **Smart OPC XML DA Module** are located
in **&lt;InstallDir&gt;\\Config\\Smart.OpcXml.Server.Configuration.xml**
file. Common configuration parameters described above are entirely valid
for the **OPC XML DA** module. Further will be discussed how to
configure which plugins to be loaded by this module at startup.

## Loading Plugins

Describing available plugins to the **Smart OPC XML DA Module** and
which of them to load at startup is made through
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.Server.Configuration.xml**"
configuration file.

*__Example:__*

```xml
<Plugin AssemblyPath="|\Plugins\Simulation\Bin\Smart.OpcXml.Plugins.Simulation.dll" Enabled="true" />
<Plugin AssemblyPath="|\Plugins\Gateway\Bin\Smart.OpcXml.Plugins.Gateway.dll" Enabled="true" />
<Plugin AssemblyPath="|\Plugins\OpcDa\Bin\Smart.OpcXml.Plugins.OpcDa.dll" Enabled="true" />
<Plugin AssemblyPath="|\Plugins\Wmi\Bin\Smart.OpcXml.Plugins.Wmi.dll" Enabled="true" />
<Plugin AssemblyPath="|\Plugins\Virtualize\Bin\Smart.OpcXml.Plugins.Virtualize.dll" Enabled="true" />
```

To configure a plugin to be loaded you need to specify the
**AssemblyPath** of the base plugin **DLL**, and to set property
**Enabled**="**true**" if you want to load it on server startup. A
"**|**" character in the beginning means that the plugin location is
relative from the root installation path (e.g. "**&lt;InstallDir&gt;**").
You can omit the "**|**" character, but then you must specify the
absolute path to the plugin assembly to be loaded. The recommended
location where to place your plugins is "**&lt;InstallDir&gt;\\Plugins**"
folder. The default plugins wich are shipped with the distribution
package are placed in the "**&lt;InstallDir&gt;\\Plugins**" folder,
otherwise they won't work. Usually plugins use common server libraries
located in "**&lt;InstallDir&gt;\\Lib**" folder. If you write your own
plugin and want to put somewhere else than "**&lt;InstallDir&gt;\\Plugins**"
you should write your own assembly resolve function in order to find and
load required assemblies.

By default **Smart OPC XML Server** loads **Simulation**, **Gateway**
and **Virtualize** **OPC XML DA** plugins at startup and the others
delivered by the installation are described but commented in the
configuration file.

## Address Space Configuration

Address space configuration basically consists of three parts --
**Browse Elements**, **Item Properties** and **Permissions**. The
address space configuration of **Smart OPC XML DA Module** and its
plugins are very similar so further when we talk about address space of
plugins we will discuss only specifics and differences if there are.

## Browse Elements Configuration

Describing browse elements visible in the server's address space is made
through
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.AddressSpace.Elements.xml**"
configuration file. The base configuration element is called
**HierarchicalBrowseElement**. It consists of the following properties:

**Name** - The name of the browse element (refer to the **OPC XML DA Specification**);

**ItemPath** - Item path of the element (refer to the **OPC XML DA Specification**);

**ItemName** - Item name of the element (refer to the **OPC XML DA
Specification**);

**IsItem** - "**true**" if the element is item, "**false**" otherwise
(refer to the **OPC XML DA Specification**);

**HasChildren** - "**true**" if it has nested elements, "**false**"
otherwise (Address space manager after reading the configuration
overrides this value regarding there are nested elements or not);

**HierarchicalBrowseElements** can be nested. Nested elements
respresents child elements.

Thus the address space tree is built. Address space configuration
(browse elements and their item properties) refers only to own browse
elements and not to browse elements exposed by loaded plugins.

**Remark:** Each element which **IsItem** property is set to "**true**"
must have corresponding item properties described in
**Smart.OpcXml.AddressSpace.ItemProperties.xml** configuration file.

## Item Properties Configuration

Describing item properties in the server's address space is made through
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.AddressSpace.ItemProperties.xml**"
configuration file.

*__Example:__*

```xml
<ItemProperties>
    <ItemName>Random.Float</ItemName>
    <ItemPath></ItemPath>
    <dataType>float</dataType>
    <accessRights>readable</accessRights>
    <scanRate>1000</scanRate>
    <euType>analog</euType>
    <description>An IEEE single-precision 32-bit floating point value.</description>
    <highEU>340282347</highEU>
    <lowEU>-340282347</lowEU>
    <highIR>340282347</highIR>
    <lowIR>-340282347</lowIR>
    <timeZone>120</timeZone>
    <value xsi:type="xsd:float" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">0</value>
    <maximumValue xsi:type="xsd:float" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">340282</maximumValue>
    <minimumValue xsi:type="xsd:float" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">-340282</minimumValue>
    <valuePrecision>4</valuePrecision>
</ItemProperties>
```

The name of the properties and their values are as specified in the
**OPC XML DA** Specification. There are mandatory fields like
"**ItemName**". For more information refer to the **OPC XML DA**
Specification.

## Address Space Permissions

**Smart.OpcXml.AddressSpace.Permissions.xml** - This **XML** file
contains permissions over the server's address space, which parts of it
are visible and which not.

*__Example:__*

```xml
<?xml version="1.0"?>
<ArrayOfAddressSpacePermission xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <AddressSpacePermission ItemPath="SomePath" ItemName="Points.*" ApplyToBranches="true" ApplyToItems="true" Allow="true" />
  <AddressSpacePermission ItemPath="SomeOtherPath" ItemName="*" ApplyToBranches="true" ApplyToItems="true" Allow="false" />
</ArrayOfAddressSpacePermission>
```

As illustrated in the example above each address space prmission has the
following properties:

**ItemPath** - Item path of the element of which the rule is applied;

**ItemName** - Item name of the element of which the rule is applied;

**ApplyToBranches** - If set to "**true**" the rule is applied to
branches;

**ApplyToItems** - If set to "**true**" the rule is applied to items;

**Allow** - If "**true**" the rule is to permit, "**false**" to deny;

Permit rules (property **Allow** = "**true**") takes precedence over
deny rules (**Allow**="**false**"). **ItemPath** and **ItemName**
properties supports wildcards like "\*" and "?".

You can allow all browsing elements which **ItemName** starts with
"**WMI.**":

*__Example:__*

```xml
<AddressSpacePermission ItemPath="" ItemName="WMI.*" ApplyToBranches="true" ApplyToItems="true" Allow="true" />
```

Or deny all elements which **ItemPath** starts with "**LOCAL.**":

*__Example:__*
```xml
<AddressSpacePermission ItemPath="LOCAL.*" ItemName="" ApplyToBranches="true" ApplyToItems="true" Allow="false" />
```

*``Remark:`` Rule is applied to branches and items if any of
**ApplyToItems** or **ApplyToBranches** is set to "**true**".
**SupportsContinuationPoint** property in
**Smart.OpcXml.Plugin.Configuration.xml** file must be set to
"**false**" if you don't want to see disallowed items on **Browse**.*

## Plugins

The **Smart OPC XML DA Module** provides an **API** for creating plugins
which can be loaded by it. **Smart OPC XML Server** comes with several
preloaded **OPC XML DA** plugins:

-   **Simulation Plugin** - Provides address spaces items which
    represents various simulated signals for testing and demonstration
    purposes;

-   **Gateway Plugin** - Provides ability for cascade-linking of **OPC
    XML DA** **Servers**;

-   **OPC DA Plugin** - Provides ability to inerop with classic **OPC
    Data Access Servers**;

-   **WMI Plugin** - Provides ability to read data through Windows
    Management Instrumentation interface;

-   **Virtualize Plugin** - Provides ability to expose virtual items in
    the server's address spaces, which values are delivered by making
    some calculations described in **C\#** scripts.

## Common Plugin's Configuration Attributes

As mentioned above the **Smart** **OPC XML DA Module** provides and
**API** for developing new **OPC XML Data Access** plugins. So there are
configuration parameters which are common for all of this type plugins.
Of course they are not mandatory and developer may override the
functionality and thus to bypass them. We must mention that [Common
Configuration Attributes](#common-configuration-attributes) of **Smart
OPC XML DA Module** are also valid here. We will describe here
additional configuration attributes only.

\[**SupportBrowse**\]

> Indicating whether plugin supports **OPC XML DA** **Browse** action:

> * **true** - allow browse actions;

> * **false** - deny browse actions;

\[**SupportGetProperties**\]

> Indicating whether plugin supports **OPC XML DA** **GetProperties** action.

> * **true** - allow get properties actions;

> * **false** - deny get properties actions;

\[**SupportRead**\]
> Indicating whether plugin supports **OPC XML DA** **Read** action.

> * **true** - allow read actions;

> * **false** - deny read actions;

\[**SupportWrite**\]

> Indicating whether plugin supports **OPC XML DA** **Write** action.\

> * **true** -- allow write actions;

> * **false** -- deny write actions;

\[**SupportSubscribe**\]

> Indicating whether plugin supports **OPC XML DA** ** Subscribe, SubscriptionCancel, SubscriptionPolledRefresh** actions.

> * **true** - allow subscribe actions;

> * **false** - deny subscribe actions;

\[**SupportGetStatus**\]

> Indicating whether plugin supports **OPC XML DA** **GetStatus** action.

> * **true** - allow get status actions;

> * **false** - deny get status actions;

\[**Alias**\]

> Plugin module alias. Each plugin loaded by the **Smart OPC XML DA
Module** must have unique alias name which is used for prefixing address
space elements **ItemPath** and **ItemName** respectively.

\[**PathSeparator**\]

> Plugin module address space path separator used for the items.

\[**OriginalPathSeparator**\]

> This is the path separator used by the classic **OPC DA** server where
the plugin is connected to. This separator will be replaced by address
space translation mechanism with the plugin module address space path
separator.