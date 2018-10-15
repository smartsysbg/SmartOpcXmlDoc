**Smart OPC HDA Plugin** is a type of **Smart OPC XML HDA Plugin**,
managed by **Smart OPC XML HDA Module**. The main purpose of this plugin
is to provide access via **OPC XML HDA** protocol to the classic
**OPC HDA** servers.

## Directory Structure
**&lt;InstallDir&gt;** - This is the base server folder. Here is
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **OpcHda** - An **OPC XML HDA/OPC HDA** wrapper plugin;

>>> **Bin** - Contains binaries of the plugin;

>>>> **AddIns** - Contains plugin addins;

>>>>> **Slot0** - Slot 0 of the Opc Hda Server Addin;

>>>>> **Slot1** - Slot 1 of the Opc Hda Server Addin;

>>>>> **... **

>>>>> **Slot14** - Slot 14 of the Opc Hda Server Addin;

>>>> **AddInSideAdapters** - Add-in side adapters' folder;

>>>> **AddInViews** - Add-in views folder;

>>>> **Contracts** - Add-ins contract;

>>>> **HostSideAdapters** - Host side adapters;

>>> **Config** - Contains configuration files of the plugin;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

Configuration attributes of the **Smart OPC HDA** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\OpcHda\\Config\\Smart.OpcXml.HdaPlugin.Configuration.xml**
file.

__Example:__

```xml
<?xml version="1.0"?>
<HdaPluginOpcHdaConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Hda.OpcHda</LoggerName>
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
  <Alias>OPC</Alias>
  <!-- Plugin module pathSeparator used for the plugin address space items path and name. -->
  <PathSeparator>.</PathSeparator>
  <!-- Plugin module OriginalPathSeparator used for the plugin address space 
  items path and name. Original path separator is replaced with path separator. -->
  <OriginalPathSeparator>.</OriginalPathSeparator>
  <!-- Interval in milliseconds of checking OpcServer modules connection state. 
  Value cannot be lower than 3000 ms. -->
  <CheckOpcServersConnectionStateInterval>3000</CheckOpcServersConnectionStateInterval>
  <!-- Interval in milliseconds to wait before to start the new add in process. Range [10000 - 120000]ms. -->
  <!-- If TcpClientChannelSocketCacheTimeout parameter in 
  Smart.OpcXml.Service.Configuration.xml configuration file is not set or is 5 seconds, then this parameter should be 30000ms. 
  If TcpClientChannelSocketCacheTimeout is 30 seconds, this parameter must be 
  set at the maximum of 120000ms. This is important if you choose to use remoting 
  proxy services OpcXmlDaRem.asmx and OpcXmlHdaRem.asmx.
  But if you use only OpcXmlDa.asmx and OpcXmlHda.asmx web service, which do not 
  use remoting proxies, then you may set this parameter to 10000ms -->
  <AddInProcessRestartWaitTime>30000</AddInProcessRestartWaitTime>

  <!-- Maximum available items to read at once via HdaReadAtTime. 0 means no 
  restriction. -->
  <MaxItemsPerHdaReadAtTime>0</MaxItemsPerHdaReadAtTime>
  <!-- Maximum available items to read at once via HdaReadProcessed. 0 means no 
  restriction. -->
  <MaxItemsPerHdaReadProcessed>0</MaxItemsPerHdaReadProcessed>
  <!-- Maximum available items to read at once via HdaReadRaw. 0 means no 
  restriction. -->
  <MaxItemsPerHdaReadRaw>0</MaxItemsPerHdaReadRaw>

  <!-- Interval in milliseconds of estimating HDA performance counters. Value 
  cannot be lower than 1000ms. -->
  <HdaPerformanceCountersEstimationInterval>60000</HdaPerformanceCountersEstimationInterval>

  <!-- Max number of HdaReadRaw requests since last counters snapshot  after that 
  the server will response with E_REJECTED on HdaReadRaw requests.  
  0 means no limitations. -->
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
  to the executing application domain. -->
  <!-- Uncomment this to enable debug traces on first chance exceptions. Use only 
  for debugging purposes. -->
  <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be attached to 
  the executing application domain. -->
  <!-- Uncomment this to enable debug traces on unhandled exceptions. Use only 
  for debugging purposes. -->
  <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->

  <!-- LongRunningRequestsLogInterval - Interval in minutes to log long runing 
  requests if detected. Minimum is 1 minute. -->
  <LongRunningRequestsLogInterval>60</LongRunningRequestsLogInterval>

  <!-- Set Enabled to "true" if you want to enable this connection. -->
  <!-- RequestExecutionTimeout - The request execution timeout in milliseconds 
  after that the connection will be considered as broken. Range [5000-180000] ms -->
  <!-- MaxLongRunningRequests - Maximum long running requests detected after that 
  the addin will be restarted. Minimum is 1. -->
  <!-- CheckConnectionStateInterval - Opc HDA server connection check interval in 
  milliseconds. Range [3000-60000]ms -->
  <OpcHdaServer Enabled="false" CheckConnectionStateInterval="3000" RequestExecutionTimeout="60000" MaxLongRunningRequests="1">
    <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
    <LoggerName>Smart.OpcXml.Plugins.Hda.OpcHda.AddIn.SWP-EPKS-410</LoggerName>

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
    <Alias>SWP-EPKS-410</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space items path 
    and name. -->
    <PathSeparator>.</PathSeparator>

    <!-- Maximum available items to read at once via HdaReadAtTime. 0 means no 
    restriction. -->
    <MaxItemsPerHdaReadAtTime>0</MaxItemsPerHdaReadAtTime>
    <!-- Maximum available items to read at once via HdaReadProcessed. 0 means no 
    restriction. -->
    <MaxItemsPerHdaReadProcessed>0</MaxItemsPerHdaReadProcessed>
    <!-- Maximum available items to read at once via HdaReadRaw. 0 means no restriction. -->
    <MaxItemsPerHdaReadRaw>0</MaxItemsPerHdaReadRaw>

    <!-- Interval in milliseconds of estimating HDA performance counters. Value 
    cannot be lower than 1000ms. -->
    <HdaPerformanceCountersEstimationInterval>60000</HdaPerformanceCountersEstimationInterval>

    <!-- Max number of HdaReadRaw requests since last counters snapshot  after 
    that the server will response with E_REJECTED on HdaReadRaw requests.  
    0 means no limitations. -->
    <MaxHdaReadRawAfterSnapshot>0</MaxHdaReadRawAfterSnapshot>
    <!--Max number of HdaReadProcessed requests since last counters snapshot 
    after that the server will response with E_REJECTED on HdaReadProcessed 
    requests. 0 means no limitations. -->
    <MaxHdaReadProcessedAfterSnapshot>0</MaxHdaReadProcessedAfterSnapshot>
    <!-- Max number of HdaReatAtTime requests since last counters snapshot after 
    that the server will response with E_REJECTED on HdaReadAtTime requests. 
    0 means no limitations. -->
    <MaxHdaReadAtTimeAfterSnapshot>0</MaxHdaReadAtTimeAfterSnapshot>
    <!-- Max number of HdaGetAggregates requests since last counters snapshot 
    after that the server will response with E_REJECTED on HdaGetAggregates 
    requests. 0 means no limitations. -->
    <MaxHdaGetAggregatesAfterSnapshot>0</MaxHdaGetAggregatesAfterSnapshot>
    <!-- Max number of HdaGetStatus requests since last counters snapshot after 
    that the server will response with E_REJECTED on HdaGetStatus requests. 
    0 means no limitations. -->
    <MaxHdaGetStatusAfterSnapshot>0</MaxHdaGetStatusAfterSnapshot>
    <!-- Max number of HdaBrowse requests since last counters snapshot after that 
    the server will response with E_REJECTED on HdaBrowse requests. 
    0 means no limitations. -->
    <MaxHdaBrowseAfterSnapshot>0</MaxHdaBrowseAfterSnapshot>
    <!-- Max number of requests since last counters snapshot after that the 
    server will response with E_REJECTED on all requests. 0 means no limitations. -->
    <MaxHdaRequestsAfterSnapshot>0</MaxHdaRequestsAfterSnapshot>

    <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
    attached to the executing application domain. -->
    <!-- Uncomment this to enable debug traces on first chance exceptions. Use 
    only for debugging purposes. -->
    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->

    <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be attached 
    to the executing application domain. -->
    <!-- Uncomment this to enable debug traces on unhandled exceptions. Use only 
    for debugging purposes. -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->

    <!-- If set to "true" invalid cast first chance exceptions will not be 
    traced. -->
    <!-- Uncomment this to disable debug tracing of invalid cast first chance 
    exceptions. -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions> -->

    <!-- If is "true" calls CoInitializeSecurity, which disables Schannel COM 
    authentication. -->
    <IntitalizeCOMSecurity>true</IntitalizeCOMSecurity>

    <!-- Sometimes OPC HDA Server like Uniformace PHD returns success result 
    after GetItemHandles call, but actually the server handle is -1, 
    and the PHD server interpets that handle as invalid.
    Is this option is set to true, the behaviour will be to retry maximum 10 
    times to obtain a valid handle delaying between retries 1 sec. -->
    <ThreatNegativeServerHandlesAsInvalid>false</ThreatNegativeServerHandlesAsInvalid>

    <!-- Additional attributes that may be used are: Username, Password, Domain, 
    ProxyUri, AlwaysUseDA20, LicenseKey -->
    <!-- UseDuplicates "true" or "false" indicates whether to duplicate 
    connection per request or to use locks. 
    This is used where is not possible to work without locks. At the end of the 
    request the connection is released.
    Prior to server license you can set maximum duplicates to be used after which 
    lock will be obtained. MaxDuplicates 0 means no restrictions. -->
<OpcHdaConnection Url="opchda://SWP-EPKS-410A/HWHsc.OPCServer" Enabled="true" 
Priority="1000" UseDuplicates="true" Username="user" Password="pass"/>
    <OpcHdaConnection Url="opchda://SWP-EPKS-410B/HWHsc.OPCServer" Enabled="true" 
    Priority="0" UseDuplicates="true" Username="user" Password="pass"/>

    <!-- Set the expected code page of incomming strings from OPC DA. -->
    <!-- <SourceCodePage>1252</SourceCodePage> -->
    <!-- Set the proper code page incomming string to be converted to. -->
    <!-- <DestinationCodePage>1251</DestinationCodePage> -->
  </OpcHdaServer>
</HdaPluginOpcHdaConfiguration>
```

Here we will describe only additional configuration attributes, because common ones are described above:

\[**AddInProcessRestartWaitTime**\]

> Interval in milliseconds to wait before to start the new add in process.
Range \[**10000** - **120000**\] ms.

> *``Remark:`` If **TcpClientChannelSocketCacheTimeout** parameter in
**Smart.OpcXml.Service.Configuration.xml** configuration file is not set
or is **5** seconds, then this parameter should be **30000ms**. If
**TcpClientChannelSocketCacheTimeout** is **30** seconds, this parameter
must be set at the maximum of **120000ms**. This is important if you
choose to use remoting proxy services **OpcXmlDaRem.asmx** and
**OpcXmlHdaRem.asmx**. But if you use only **OpcXmlDa.asmx** and
**OpcXmlHda.asmx** web service, which do not use remoting proxies, then
you may set this parameter to **10000ms**.*

\[**CheckOpcServersConnectionStateInterval**\]

> Interval in milliseconds for checking **OpcServer** modules connnection
state. Value cannot be lower than 3000 ms.

\[**LongRunningRequestsLogInterval**\]

> Interval in minutes to log long runing requests if detected. Minimum is
1 minute.

\[**OpcHdaServer**\]

> **OPC HDA** plugin module supports multiple connections to **OPC HDA**
servers. Each connection is configured via a separate "**OpcHdaServer**"
section.

## Configuring connections to OPC HDA Servers

**OPC HDA** plugin supports multiple connections to **OPC HDA** servers.
Each connection is configured via a separate "**OpcHdaServer**" section
in the plugin configuration file
**&lt;InstallDir&gt;\\Plugins\\OpcHda\\Config\\Smart.OpcXml.HdaPlugin.Configuration.xml**.

__Example:__

```xml
  <!-- Set Enabled to "true" if you want to enable this connection. -->
  <!-- RequestExecutionTimeout - The request execution timeout in milliseconds 
  after that the connection will be considered as broken. Range [5000-180000] ms -->
  <!-- MaxLongRunningRequests - Maximum long running requests detected after that 
  the addin will be restarted. Minimum is 1. -->
  <!-- CheckConnectionStateInterval - Opc HDA server connection check interval in 
  milliseconds. Range [3000-60000]ms -->
  <OpcHdaServer Enabled="false" CheckConnectionStateInterval="3000" 
  RequestExecutionTimeout="60000" MaxLongRunningRequests="1">
    <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
    <LoggerName>Smart.OpcXml.Plugins.Hda.OpcHda.AddIn.MTKN$LOCAL</LoggerName>

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
    <Alias>MTKN$LOCAL</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space items path 
    and name. -->
    <PathSeparator>.</PathSeparator>

    <!-- Maximum available items to read at once via HdaReadAtTime. 0 means no 
    restriction. -->
    <MaxItemsPerHdaReadAtTime>0</MaxItemsPerHdaReadAtTime>
    <!-- Maximum available items to read at once via HdaReadProcessed. 0 means no 
    restriction. -->
    <MaxItemsPerHdaReadProcessed>0</MaxItemsPerHdaReadProcessed>
    <!-- Maximum available items to read at once via HdaReadRaw. 0 means no 
    restriction. -->
    <MaxItemsPerHdaReadRaw>0</MaxItemsPerHdaReadRaw>

    <!-- Interval in milliseconds of estimating HDA performance counters. Value 
    cannot be lower than 1000ms. -->
    <HdaPerformanceCountersEstimationInterval>60000</HdaPerformanceCountersEstimationInterval>

    <!-- Max number of HdaReadRaw requests since last counters snapshot  after 
    that the server will response with E_REJECTED on HdaReadRaw requests.  
    0 means no limitations. -->
    <MaxHdaReadRawAfterSnapshot>0</MaxHdaReadRawAfterSnapshot>
    <!--Max number of HdaReadProcessed requests since last counters snapshot 
    after that the server will response with E_REJECTED on HdaReadProcessed 
    requests. 0 means no limitations. -->
    <MaxHdaReadProcessedAfterSnapshot>0</MaxHdaReadProcessedAfterSnapshot>
    <!-- Max number of HdaReatAtTime requests since last counters snapshot after 
    that the server will response with E_REJECTED on HdaReadAtTime requests. 
    0 means no limitations. -->
    <MaxHdaReadAtTimeAfterSnapshot>0</MaxHdaReadAtTimeAfterSnapshot>
    <!-- Max number of HdaGetAggregates requests since last counters snapshot 
    after that the server will response with E_REJECTED on HdaGetAggregates 
    requests. 0 means no limitations. -->
    <MaxHdaGetAggregatesAfterSnapshot>0</MaxHdaGetAggregatesAfterSnapshot>
    <!-- Max number of HdaGetStatus requests since last counters snapshot after 
    that the server will response with E_REJECTED on HdaGetStatus requests. 
    0 means no limitations. -->
    <MaxHdaGetStatusAfterSnapshot>0</MaxHdaGetStatusAfterSnapshot>
    <!-- Max number of HdaBrowse requests since last counters snapshot after that 
    the server will response with E_REJECTED on HdaBrowse requests. 
    0 means no limitations. -->
    <MaxHdaBrowseAfterSnapshot>0</MaxHdaBrowseAfterSnapshot>
    <!-- Max number of requests since last counters snapshot after that the 
    server will response with E_REJECTED on all requests. 0 means no limitations. -->
    <MaxHdaRequestsAfterSnapshot>0</MaxHdaRequestsAfterSnapshot>

    <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
    attached to the executing application domain. -->
    <!-- Uncomment this to enable debug traces on first chance exceptions. Use 
    only for debugging purposes. -->
    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->

    <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be attached 
    to the executing application domain. -->
    <!-- Uncomment this to enable debug traces on unhandled exceptions. Use only 
    for debugging purposes. -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->

    <!-- If set to "true" invalid cast first chance exceptions will not be 
    traced. -->
    <!-- Uncomment this to disable debug tracing of invalid cast first chance 
    exceptions. -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions> -->

    <!-- Sometimes OPC HDA Server like Uniformace PHD returns success result 
    after GetItemHandles call, but actually the server handle is -1, 
    and the PHD server interpets that handle as invalid.
    Is this option is set to true, the behaviour will be to retry maximum 10 
    times to obtain a valid handle delaying between retries 1 sec. -->
    <ThreatNegativeServerHandlesAsInvalid>false</ThreatNegativeServerHandlesAsInvalid>

    <!-- If is "true" calls CoInitializeSecurity, which disables Schannel COM 
    authentication. -->
    <IntitalizeCOMSecurity>false</IntitalizeCOMSecurity>

    <!-- Additional attributes that may be used are: Username, Password, Domain, 
    ProxyUri, LicenseKey -->
    <!-- UseDuplicates "true" or "false" indicates whether to duplicate 
    connection per request or to use locks. 
    This is used where is not possible to work without locks. At the end of the 
    request the connection is released.
    Prior to server license you can set maximum duplicates to be used after which 
    lock will be obtained. MaxDuplicates 0 means no restrictions. -->
    <OpcHdaConnection Url ="opchda://localhost/Matrikon.OPC.Simulation" 
    Enabled="true" Priority="1000" UseDuplicates="true" MaxDuplicates="5"/>
    <!-- <OpcHdaConnection Url="" Enabled="false" Priority="0"/> -->

    <!-- Set the expected code page of incomming strings from OPC DA. -->
    <!-- <SourceCodePage>1252</SourceCodePage> -->
    <!-- Set the proper code page incomming string to be converted to. -->
    <!-- <DestinationCodePage>1251</DestinationCodePage> -->
  </OpcHdaServer>
```

As you see most of the addin configuration parameters are the same like
these of the **OPC HDA** plugin module, that's why we will explain here
only additional ones:

\[**DebugTraceIgnoreInvalidCastFirstChanceExceptions**\]

> If is set to "**true**" invalid cast exceptions will not be traced by
first chance exceptions handler.\
> *``Remark:`` Use this feature only for debugging purposes. It does matter
only if "**DebugTraceFirstChanceExceptions"** is turned on by setting it
to "**true**".*

\[**IntitalizeCOMSecurity**\]

> If is "**true**" **CoInitializeSecurity** is called, which disables
**Schannel COM** authentication.

> *``Remark:`` Use this if the **Smart OPC XML Server** process is running
under credentials that do not have access to the classic **OPC HDA**
Server. In this case you have to provide username and password for
connecting to the classic **OPC HDA** server and **InitializeCOMSecurity** must be turned on, to disable **Schannel COM** authentication, thus the **OPC XML Server** process identity will not be used for impersonating **DCOM** requests.*

\[**Enabled**\]

> If is set to "**true**" the specified **OpcHdaServer** is enabled,
otherwise is disabled;

\[**SourceCodePage**\]

> Sets the expected code page of incomming strings from **OPC HDA**. Used
in very rare situations when **DCOM** server cannot properly translate
strings into proper code page. Usually is commented.

\[**DestinationCodePage**\]

> Set the proper code page incomming string to be converted to. Used in
very rare situations when **DCOM** server cannot properly translate
strings into proper code page. Usually is commented.

\[**CheckConnectionStateInterval**\]

> Interval in milliseconds for checking **OpcHdaServer** connnection
state. Value cannot be lower than 3000 ms.

\[**RequestExecutionTimeout**\]

> The request execution timeout in milliseconds after that the connection
will be considered as broken. Range \[5000-180000\] ms.

\]**MaxLongRunningRequests**\]

> Maximum long running requests detected after that the addin will be
restarted. Minimum is 1.

\[**OpcHdaConnection**\]

> The **OpcHdaConnection** attribute is used to specify coonection enpoint
to the classic **OPC HDA Server**. You can connect to **DCOM** server
which supports **OPC HDA** protocol version. You can specify several **OpcHdaConnection** attributes and prioritize them by using the "**Priority**" attribute of the **OpcHdaConnection**. The bigger values means higher prioriry. Specifying several **OpcHdaConnection** attributes is used for specifiying redundand connection points or servers. If one connection becomes broken then the
others ordered by "**Priority**" will be tested to establish connection.

Here are the attributes of **OpcHdaConnection**:

> * **Url** - **OPC HDA** Server endpoint address. The format is "**opchda://computer name or ip address/DCOM service name or GUID**".
Enpoint address starts always with prefix "**opchda://**". After the
prefix you must point computer name (if you specify computer name,
remember that the name must be able to be translated to an **IP**
address, so check if the **DNS** will resolve it or if you don't use
**DNS** services, be sure to be specified in the computer hosts file) or
**IP** address. Finally you must point the **DCOM** service name or it's
**GUID**;

> * **Enabled** - If is set to "**true**" the specified **OpcHdaConnection** is enabled, otherwise is disabled;

> * **Priority** - Priority of the **OpcHdaConnection**, higher values
means higher priority. When the current connection is broken the
**OpcHdaConnection** with higher priorities will be tested first;

> * **Username** - Credential username for impersonating to the **OPC HDA**
server (conisder turning on **InitializeCOMSecurity**);

> * **Password** - Credential password for impersonating to the **OPC HDA**
server (conisder turning on **InitializeCOMSecurity**);

> * **Domain** - Credential domain for impersonating to the **OPC HDA**
server (conisder turning on **InitializeCOMSecurity**);

> * **ProxyUri** - Specify a proxy address if your connection passes
through;

> * **LicesneKey** - Put the licence key here if you have such for
connecting to the **OPC HDA** server;

> * **UseDiplicates** - If is set to "**true**" then when browsing the
server address space, each user will use a separate connection which is
opened and closed after the request finishes. Thus address space
browsings are made concurrently in other case users requests are
executed consequently;

> * **MaxDuplicates** - Prior to server license you can set the maximum
number of duplicated connections to be used after exhausting it the
users browse requests will be executed consequently. 0 means no
restrictions.

__Example:__

```xml
  <OpcHdaServer Enabled="false" CheckConnectionStateInterval="3000" 
  RequestExecutionTimeout="60000" MaxLongRunningRequests="1">
    <LoggerName>Smart.OpcXml.Plugins.Hda.OpcHda.AddIn.SWP-EPKS-410</LoggerName>
    <SupportHdaReadRaw>true</SupportHdaReadRaw>
    <SupportHdaReadProcessed>true</SupportHdaReadProcessed>
    <SupportHdaReadAtTime>true</SupportHdaReadAtTime>
    <SupportHdaGetAggregates>true</SupportHdaGetAggregates>
    <SupportHdaGetStatus>true</SupportHdaGetStatus>
    <SupportHdaBrowse>true</SupportHdaBrowse>
    <Alias>SWP-EPKS-410</Alias>
    <PathSeparator>.</PathSeparator>
    <MaxItemsPerHdaReadAtTime>0</MaxItemsPerHdaReadAtTime>
    <MaxItemsPerHdaReadProcessed>0</MaxItemsPerHdaReadProcessed>
    <MaxItemsPerHdaReadRaw>0</MaxItemsPerHdaReadRaw>
    <HdaPerformanceCountersEstimationInterval>60000</HdaPerformanceCountersEstimationInterval>
    <MaxHdaReadRawAfterSnapshot>0</MaxHdaReadRawAfterSnapshot>
    <MaxHdaReadProcessedAfterSnapshot>0</MaxHdaReadProcessedAfterSnapshot>
    <MaxHdaReadAtTimeAfterSnapshot>0</MaxHdaReadAtTimeAfterSnapshot>
    <MaxHdaGetAggregatesAfterSnapshot>0</MaxHdaGetAggregatesAfterSnapshot>
    <MaxHdaGetStatusAfterSnapshot>0</MaxHdaGetStatusAfterSnapshot>
    <MaxHdaBrowseAfterSnapshot>0</MaxHdaBrowseAfterSnapshot>
    <MaxHdaRequestsAfterSnapshot>0</MaxHdaRequestsAfterSnapshot>
    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions> -->
    <IntitalizeCOMSecurity>true</IntitalizeCOMSecurity>
    <ThreatNegativeServerHandlesAsInvalid>false</ThreatNegativeServerHandlesAsInvalid>
<OpcHdaConnection Url="opchda://SWP-EPKS-410A/HWHsc.OPCServer" Enabled="true" 
Priority="1000" UseDuplicates="true" Username="user" Password="pass"/>
    <OpcHdaConnection Url="opchda://SWP-EPKS-410B/HWHsc.OPCServer" Enabled="true" 
    Priority="0" UseDuplicates="true" Username="user" Password="pass"/>
    <!-- <SourceCodePage>1252</SourceCodePage> -->
    <!-- <DestinationCodePage>1251</DestinationCodePage> -->
  </OpcHdaServer>
```


## AddIn Slots

Each enabled **OPC HDA Server** configuration, described in
**OpcHdaServer** sections, is raised in a separate addin process using
managed add-in framework. Because of technology constraint it is not
possible to raise two addin processes from the same place. That's the
reason why we use slots for each addin process. The number of available
slots must be greater or equal to the number enabled **OpcHdaServer**
configurations. In other case some of the **OpcHdaServer**
configurations will remain down due to lack of slots. The **Smart OPC
XML Server OPC HDA** plugin comes with initially prepared 15 slots
situated in

**&lt;InstallDir&gt;** - This is the base server folder. Here is situated
the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **OpcHda** - An **OPC XML HDA/OPC HDA** wrapper plugin module;

>>> **Bin** - Contains binaries of the plugin module;

>>>> **AddIns** - Contains plugin module addins;

>>>> **Slot0** - Slot 0 of the Opc Hda Server Addin;

>>>> **Slot1** - Slot 1 of the Opc Hda Server Addin;

>>>> **... **

>>>> **Slot14** - Slot 14 of the Opc Hda Server Addin;

You can increase available slots like creating a new folder (beneath
**AddIns** where the other slots are placed ) named for example
**Slot15** and copy all content of the **Slot0** folder into the new one
(**Slot15**).