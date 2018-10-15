**Smart OPC XML Server** provides two basic data access modules -
**Smart OPC XML Data Access** and **Smart OPC XML Historical Data
Access**. **Smart OPC XML HDA Module** is one of the basic parts of the
entire **Smart OPC XML Server**. Configuration of the **Smart OPC XML HDA** module is in **XML** configuration file situated in
**&lt;InstallDir&gt;\\Config** folder.

## Common Configuration Attributes

**Smart OPC XML HDA Module** provides an **API** for developing new
**OPC XML Historical Data Access** plugins. So there are configuration
parameters which are common for the module and all of this type plugins.
Of course they are not mandatory and developer may override the
functionality and thus to bypass them.

\[**LoggerName**\]

> Provides the **NLog** logger name. If empty or omitted null logger will
be used instead.

\[**MaxItemsPerHdaReadAtTime**\]

> Maximum available items to read at once via **HdaReadAtTime**. 0 means
no restriction.

\[**MaxItemsPerHdaReadProcessed**\]

> Maximum available items to read at once via **HdaReadProcessed**. 0
means no restriction.

\[**MaxItemsPerHdaReadRaw**\]

> Maximum available items to read at once via **HdaReadRaw**. 0 means no
restriction.

\[**HdaPerformanceCountersEstimationInterval**\]

> Interval in milliseconds of estimating **HDA** performance counters. Value cannot be lower than 1000ms.

\[**MaxHdaReadRawAfterSnapshot**\]

> Max allowed **HdaReadRaw** requests since last counters snapshot (i.e.
max number of requests are per specified performance counters estimation
interval). 0 means no limit. **E\_REJECTED** is thrown if the limit is
reached.

\[**MaxHdaReadProcessedAfterSnapshot**\]

> Max allowed **HdaReadProcessed** requests since last counters snapshot
(i.e. max number of requests are per specified performance counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxHdaReadAtTimeAfterSnapshot**\]

> Max allowed **HdaReadAtTime** requests since last counters snapshot
(i.e. max number of requests are per specified performance counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxHdaGetAggregatesAfterSnapshot**\]

> Max allowed **HdaGetAggregates** requests since last counters snapshot
(i.e. max number of requests are per specified performance counters
estimation interval). 0 means no limit. **E\_REJECTED** is thrown if the
limit is reached.

\[**MaxHdaGetStatusAfterSnapshot**\]

> Max allowed **HdaGetStatus** requests since last counters snapshot (i.e.
max number of requests are per specified performance counters estimation
interval). 0 means no limit. **E\_REJECTED** is thrown if the limit is
reached.

\[**MaxHdaBrowseAfterSnapshot**\]

> Max allowed **HdaBrowse** requests since last counters snapshot (i.e.
max number of requests are per specified performance counters estimation
interval). 0 means no limit. **E\_REJECTED** is thrown if the limit is
reached.

\[**MaxHdaRequestsAfterSnapshot**\]

> Max allowed requests since last counters snapshot (i.e. max number of
requests are per specified performance counters estimation interval).
Must be consistent with other requests type limitations. 0 means no
limit. **E\_REJECTED** is thrown if the limit is reached.

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

Configuration attributes of the **Smart OPC XML HDA Module** are located
in **&lt;InstallDir&gt;\\Config\\Smart.OpcXml.HdaServer.Configuration.xml**
file. Common configuration parameters described above are entirely valid
for the **OPC XML HDA** module. Further will be discussed how to
configure which plugins to be loaded by this module at startup.

## Loading Plugins

Describing available plugins to the **Smart OPC XML HDA Module** and
which of them to load at startup is made through
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.HdServer.Configuration.xml**"
configuration file.

__Example:__

```xml
   <Plugin AssemblyPath="|\Plugins\OpcHda\Bin\Smart.OpcXml.Plugins.Hda.OpcHda.dll" Enabled="true" /> 
   <Plugin AssemblyPath="|\Plugins\HdaGateway\Bin\Smart.OpcXml.Plugins.Hda.HdaGateway.dll" Enabled="true" /> 
   <Plugin AssemblyPath="|\Plugins\HdaVirtualize\Bin\Smart.OpcXml.Plugins.Hda.HdaVirtualize.dll" Enabled="true" /> 
```

To configure a plugin to be loaded you need to specify the
**AssemblyPath** of the base plugin **DLL**, and to set property
**Enabled**="**true**" if you want to load it on server startup. A
"**\|**" character in the beginning means that the plugin location is
relative from the root installation path (e.g. "****").
You can omit the "**\|**" character, but then you must specify the
absolute path to the plugin assembly to be loaded. The recommended
location where to place your plugins is "**\\Plugins**"
folder. The default plugins wich are shipped with the distribution
package are placed in the "**\\Plugins**" folder,
otherwise they won't work. Usually plugins use common server libraries
located in "**\\Lib**" folder. If you write your own
plugin and want to put somewhere else than "**\\Plugins**"
you should write your own assembly resolve function in order to find and
load required assemblies.

By default **Smart OPC XML Server** does not load any **OPC XML HDA**
plugins at startup. Delivered plugins by the installation are commented
in the configuration file (**OpcHda**, **HdaGateway** and
**HdaVirtualize**).

## Plugins

The **Smart OPC XML HDA Module** provides an **API** for creating
plugins which can be loaded by it. **Smart OPC XML Server** comes with
several preloaded **OPC XML HDA** plugins:

-   **HDA Gateway Plugin** - Provides ability for cascade-linking of
    **OPC XML HDA** **Servers**;

-   **OPC HDA Plugin** - Provides ability to inerop with classic **OPC
    Historical Data Access Servers**;

-   **HDA Virtualize Plugin** - Provides ability to expose virtual
    items in the server's address spaces, which values are delivered by
    making some calculations described in **C\#** scripts.

## Common Plugin's Configuration Attributes

As mentioned above the **Smart OPC XML HDA Module** provides and
**API** for developing new **OPC XML Historical Data Access** plugins.
So there are configuration parameters which are common for all of this
type plugins. Of course they are not mandatory and developer may
override the functionality and thus to bypass them. We must mention that
[Common Configuration Attributes](#common-configuration-attributes) of
**Smart OPC XML HDA Module** are also valid here. We will describe here
additional configuration attributes only.

\[**SupportHdaReadRaw**\]

> Indicating whether plugin supports **HdaReadRaw**
action:

> * **true** - allow browse actions;

> * **false** - deny browse actions;

\[**SupportHdaReadProcessed**\]

> Indicating whether plugin supports **HdaReadProcessed** action.

> * **true** - allow get properties actions;

> * **false** - deny get properties actions;

\[**SupportHdaReadAtTime**\]

> Indicating whether plugin supports **HdaReadAtTime** action.

> * **true** - allow read actions;

> * **false** - deny read actions;

\[**SupportHdaGetAggregates**\]

> Indicating whether plugin supports **HdaGetAggregates** action.

> * **true** - allow write actions;

> * **false** - deny write actions;

\[**SupportHdaGetStatus**\]

> Indicating whether plugin supports **HdaGetStatus** action.

> * **true** - allow subscribe actions;

> * **false** - deny subscribe actions;

\[**SupportHdaBrowse**\]

> Indicating whether plugin supports **HdaBrowse** action.

> * **true** - allow get status actions;

> * **false** - deny get status actions;

\[**Alias**\]

> Plugin module alias. Each plugin loaded by the **Smart OPC XML HDA
Module** must have unique alias name which is used for prefixing address
space elements **ItemPath** and **ItemName** respectively.

\[**PathSeparator**\]

> Plugin module address space path separator used for the items.

\[**OriginalPathSeparator**\]

> This is the path separator used by the classic **OPC HDA** server where
the plugin is connected to. This separator will be replaced by address
space translation mechanism with the plugin module address space path
separator.