**Smart OPC DA Plugin** is a type of **Smart** **OPC XML DA Plugin**,
managed by **Smart OPC XML DA Module**. The main purpose of this plugin
is to provide access via **OPC XML** protocol to the classic **OPC DA**
servers.

## Directory Structure

**&lt;InstallDir&gt;** - This is the base server folder. Here is
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **OpcDa** - An **OPC XML DA/OPC DA** wrapper plugin;

>> **Bin** - Contains binaries of the plugin;

>> **AddIns** - Contains plugin addins;

>>> **Slot0** - Slot 0 of the Opc Server Addin;

>>> **Slot1** - Slot 1 of the Opc Server Addin;

>>> **... **

>>> **Slot14** - Slot 14 of the Opc Server Addin;

>> **AddInSideAdapters** - Add-in side adapters' folder;

>> **AddInViews** - Add-in views folder;

>> **Contracts** - Add-ins contract;

>> **HostSideAdapters** - Host side adapters;

>> **Config** - Contains configuration files of the plugin;

>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **Smart** **OPC DA** plugin configuration is separated in several
**XML** configuration files situated in
**&lt;InstallDir&gt;\\Plugins\\OpcDa\\Config** folder. Configuration
attributes of the **Smart OPC DA** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\OpcDa\\Config\\Smart.OpcXml.Plugin.Configuration.xml**
file.

*__Example:__*

```xml
<?xml version="1.0"?>
<PluginOpcDaConfiguration 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead.  -->
  <LoggerName>Smart.OpcXml.Plugins.OpcDa</LoggerName>
  <!-- Value indicating whether plugin supports browse.  -->
  <SupportBrowse>true</SupportBrowse>
  <!-- Value indicating whether plugin supports get properties  -->
  <SupportGetProperties>true</SupportGetProperties>
  <!-- Value indicating whether plugin supports read.  -->
  <SupportRead>true</SupportRead>
  <!-- Value indicating whether plugin supports write.  -->
  <SupportWrite>true</SupportWrite>
  <!-- Value indicating whether plugin supports subscribe.  -->
  <SupportSubscribe>true</SupportSubscribe>
  <!-- Value indicating whether plugin supports get status.  -->
  <SupportGetStatus>true</SupportGetStatus>
  <!-- Plugin module alias.  -->
  <Alias>OPC</Alias>
  <!-- Plugin module pathSeparator used for the plugin address space items path and name.  -->
  <PathSeparator>.</PathSeparator>
  <!-- Plugin module OriginalPathSeparator used for the plugin address 
  space items path and name. Original path separator is replaced with path 
  separator.  -->
  <OriginalPathSeparator>.</OriginalPathSeparator>
  <!-- Minimum requested sampling rate in milliseconds. Value cannot be 
  lower than 1000 ms.  -->
  <MinSubscriptionSamplingRate>1000</MinSubscriptionSamplingRate>
  <!-- Default requested sampling rate in milliseconds if such is not 
  specified. Value cannot be lower than 1000 ms.  -->
  <DefaultSubscriptionSamplingRate>3000</DefaultSubscriptionSamplingRate>
  <!-- Buffer size of each subscribe request item. Used when 
  EnableBuffering is specified in Subscribe. Cannot be lower than 2.  -->
  <MaxSubscriptionItemBufferSize>10</MaxSubscriptionItemBufferSize>
  <!-- Default SubscriptionPingRate in milliseconds if such is not 
  specified in Subscribe. Range [10 000;300 000] ms. -->
  <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
  <!-- The maximum subscribe lists. After reaching that value, the server 
  will not execute subscribes any more until 
  total count of subscribed lists in the server becomes less than that 
  value. MaxSubscriptions cannot be lower than 10.  -->
  <MaxSubscriptions>1000</MaxSubscriptions>
  <!-- Maximum allowed number of items per subscribe list.Cannot be lower 
  than 50  -->
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
  subscribe request items for new values.DataRefreshInterval cannot be 
  lower than 100ms.  -->
  <DataRefreshInterval>100</DataRefreshInterval>
  <!-- Interval in milliseconds that subscriptions manager should check for 
  and clean expired subscriptions. 
  CleanExpiredSubscriptionsInterval cannot be lower than 1000ms.  -->
  <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
  <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be greater 
  than 50000 ms.  -->
  <MaxHoldTime>50000</MaxHoldTime>
  <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime cannot 
  be greater than 50000ms.  -->
  <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>
  <!-- How many subscriptions should be evaluated by one thread in 
  subscriptions manager. Value cannot be lower than 50.  -->
  <EvaluatedSubscriptionsPerThread>400</EvaluatedSubscriptionsPerThread>
  <!-- Maximum items to be read  at once in order to refresh subscriptions 
  data by subscriptions manager.  -->
  <MaxRefreshedItemsAtOnce>100</MaxRefreshedItemsAtOnce>
  <!-- Initial capacity of read buffer cache. Specify count of samples.  -->
  <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
  <!-- Maximum capacity of read buffer cache. Specify count of samples.  -->
  <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>
  <!-- Interval in milliseconds of estimating performance counters. Value 
  cannot be lower than 1000 ms.  -->
  <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>
  <!-- Interval in milliseconds of estimating read buffer cache counters. 
  Value cannot be lower than 1000 ms.  -->
  <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>
  <!-- Interval in milliseconds of estimating subscriptions manager 
  counters. Value cannot be lower than 1000 ms.  -->
  <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>
  <!-- Interval in milliseconds of checking OpcServer modules connection 
  state. Value cannot be lower than 3000 ms.  -->
  <CheckOpcServersConnectionStateInterval>3000</CheckOpcServersConnectionStateInterval>
  <!-- Interval in milliseconds to wait before to start the new add in 
  process. Range [10000 - 120000]ms. -->
  <!-- If TcpClientChannelSocketCacheTimeout parameter in 
  Smart.OpcXml.Service.Configuration.xml configuration file 
  is not set or is 5 seconds, then this parameter should be 30000ms. If 
  TcpClientChannelSocketCacheTimeout is 30 seconds, this parameter 
  must be set at the maximum of 120000ms. This is important if you choose 
  to use remoting proxy services OpcXmlDaRem.asmx and OpcXmlHdaRem.asmx. 
  But if you use only OpcXmlDa.asmx and OpcXmlHda.asmx web service, which 
  do not use remoting proxies, then you may set this 
  parameter to 10000ms -->
  <AddInProcessRestartWaitTime>30000</AddInProcessRestartWaitTime>

  <!-- The following limitations are per estimation interval!  -->
  <!-- Maximum allowed read requests since last counters snapshot. 0 means 
  no limit.  -->
  <MaxReadAfterSnapshot>0</MaxReadAfterSnapshot>
  <!-- Maximum allowed write requests since last counters snapshot. 0 means no limit.  -->
  <MaxWriteAfterSnapshot>0</MaxWriteAfterSnapshot>
  <!-- Maximum allowed subscribe requests since last counters snapshot. 0 
  means no limit.  -->
  <MaxSubscribeAfterSnapshot>0</MaxSubscribeAfterSnapshot>
  <!-- Maximum subscription polled refresh requests since last counters 
  snapshot. 0 means no limit.  -->
  <MaxPolledRefreshAfterSnapshot>0</MaxPolledRefreshAfterSnapshot>
  <!-- Maximum allowed browse requests since last counters snapshot. 0 
  means no limit.  -->
  <MaxBrowseAfterSnapshot>0</MaxBrowseAfterSnapshot>
  <!-- Maximum allowed get status requests since last counters snapshot. 0 means no limit.  -->
  <MaxGetStatusAfterSnapshot>0</MaxGetStatusAfterSnapshot>
  <!-- Maximum allowed get properties requests since last counters 
  snapshot. 0 means no limit.  -->
  <MaxGetPropertiesAfterSnapshot>0</MaxGetPropertiesAfterSnapshot>
  <!-- Maximum allowed subscription cancels since last counters snapshot. 0 
  means no limit.  -->
  <MaxSubscriptionCancelAfterSnapshot>0</MaxSubscriptionCancelAfterSnapshot>
  <!-- Maximum allowed requests since last counters snapshot. 0 means no 
  limit. Must be consistent with other requests type limitations. -->
  <MaxRequestsAfterSnapshot>0</MaxRequestsAfterSnapshot>

  <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment to enable tracing of first chance exceptions  -->
  <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>  -->

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment to enable tracing of unhandled exceptions  -->
  <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>  -->

  <!-- LongRunningRequestsLogInterval - Interval in minutes to log long 
  runing requests if detected. Minimum is 1 minute. -->
  <LongRunningRequestsLogInterval>60</LongRunningRequestsLogInterval>

  <!-- Set Enabled to "true" if you have locally installed Matrikon OPC DA 
  simulation server -->
  <!-- RequestExecutionTimeout - The request execution timeout in 
  milliseconds after that the connection will be considered as broken. 
  Range [5000-180000] ms -->
  <!-- MaxLongRunningRequests - Maximum long running requests detected 
  after that the addin will be restarted. Minimum is 1. -->
  <!-- CheckConnectionStateInterval - Opc DA server connection check 
  interval in milliseconds. Range [3000 - 60000]ms -->
  <!-- ValidateItemsBeforeSubscribe - if true items will be validated 
  through group before adding to it. -->
  <!-- DA20ValidateItemsAfterBrowse - If is set "true" returned items from 
  browse will be validate. (DA20 only) -->
  <!-- DA20BrowseEnumeratorBlockSize - Specifies address space browse 
  enumerator how many items to fetch at once. (Range from 10 to 10000). 
  (DA20 only) -->
  <!-- MTKN$LOCAL -->
  <OpcServer Enabled="false" CheckConnectionStateInterval="3000" 
  RequestExecutionTimeout="60000" MaxLongRunningRequests="1" 
  ValidateItemsBeforeSubscribe="true">
    <!-- NLog logger name. If empty or omitted the null logger will be used 
    instead.  -->
    <LoggerName>Smart.OpcXml.Plugins.OpcDa.AddIn.MTKN$LOCAL</LoggerName>
    <!-- Value indicating whether plugin supports browse.  -->
    <SupportBrowse>true</SupportBrowse>
    <!-- Value indicating whether plugin supports get properties  -->
    <SupportGetProperties>true</SupportGetProperties>
    <!-- Value indicating whether plugin supports read.  -->
    <SupportRead>true</SupportRead>
    <!-- Value indicating whether plugin supports write.  -->
    <SupportWrite>true</SupportWrite>
    <!-- Value indicating whether plugin supports subscribe.  -->
    <SupportSubscribe>true</SupportSubscribe>
    <!-- Value indicating whether plugin supports get status.  -->
    <SupportGetStatus>true</SupportGetStatus>
    <!-- Specifies if plugin module supports continuation points. If is set 
    to "true" address space permissions will not be applied on Browse 
    response. -->
    <SupportsContinuationPoint>true</SupportsContinuationPoint>
    <!-- Plugin module alias.  -->
    <Alias>MTKN$LOCAL</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space 
    items path and name.  -->
    <PathSeparator>.</PathSeparator>
    <!-- Minimum requested sampling rate in milliseconds. Value cannot be 
    lower than 1000 ms.  -->
    <MinSubscriptionSamplingRate>1000</MinSubscriptionSamplingRate>
    <!-- Default requested sampling rate in milliseconds if such is not 
    specified. Value cannot be lower than 1000 ms.  -->
    <DefaultSubscriptionSamplingRate>3000</DefaultSubscriptionSamplingRate>
    <!-- Buffer size of each subscribe request item. Used when 
    EnableBuffering is specified in Subscribe. Cannot be lower than 2.  -->
    <MaxSubscriptionItemBufferSize>10</MaxSubscriptionItemBufferSize>
    <!-- Default SubscriptionPingRate in milliseconds if such is not 
    specified in Subscribe. Range [10 000;300 000] ms. -->
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <!-- The maximum subscribe lists. After reaching that value, the server 
    will not execute subscribes any more until 
    total count of subscribed lists in the server becomes less than that 
    value. MaxSubscriptions cannot be lower than 10.  -->
    <MaxSubscriptions>1000</MaxSubscriptions>
    <!-- Maximum allowed number of items per subscribe list.Cannot be lower than 50  -->
    <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
    <!-- Maximum allowed number of items per read list. 0 if no restrictions -->
    <MaxItemsPerRead>0</MaxItemsPerRead>
    <!-- Maximum allowed number of items per write list. 0 if no restrictions -->
    <MaxItemsPerWrite>0</MaxItemsPerWrite>
    <!-- Maximum allowed number of items per get properties list. 0 if no restrictions -->
    <MaxItemsPerGetProperties>0</MaxItemsPerGetProperties>
    <!-- The maximum items returned per browse request. If value is greater 
    than 0, and MaxElementsReturned is 0 or greater than MaxItemsPerBrowse 
    it will be forced to this value. If 0 there is no constraint.
        SupportsContiunationPoint must be set to "true" in order the 
        restriction to be taken into account for this gateway. -->
    <MaxItemsPerBrowse>0</MaxItemsPerBrowse>

    <!-- Interval in milliseconds that subscriptions manager should check 
    for and clean expired subscriptions. CleanExpiredSubscriptionsInterval 
    cannot be lower than 1000ms.  -->
    <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
    <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be 
    greater than 50000 ms.  -->
    <MaxHoldTime>50000</MaxHoldTime>
    <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime 
    cannot be greater than 50000ms.  -->
    <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>

    <!-- Initial capacity of read buffer cache. Specify count of samples.  -->
    <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
    <!-- Maximum capacity of read buffer cache. Specify count of samples.  -->
    <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>

    <!-- Interval in milliseconds of estimating read buffer cache counters. 
    Value cannot be lower than 1000 ms.  -->
    <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>  

    <!-- Interval in milliseconds of estimating subscriptions manager 
    counters. Value cannot be lower than 1000 ms.  -->
    <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>  

    <!-- Interval in milliseconds of estimating performance counters. Value 
    cannot be lower than 1000 ms. -->
    <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>

    <!-- The following limitations are per estimation interval! -->
    <!-- Maximum allowed read requests since last counters snapshot. 0 
    means no limit. -->
    <MaxReadAfterSnapshot>0</MaxReadAfterSnapshot>
    <!-- Maximum allowed write requests since last counters snapshot. 0 
    means no limit. -->
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
    <!-- Maximum allowed get status requests since last counters snapshot. 
    0 means no limit. -->
    <MaxGetStatusAfterSnapshot>0</MaxGetStatusAfterSnapshot>
    <!-- Maximum allowed get properties requests since last counters 
    snapshot. 0 means no limit. -->
    <MaxGetPropertiesAfterSnapshot>0</MaxGetPropertiesAfterSnapshot>
    <!-- Maximum allowed subscription cancels since last counters snapshot. 
    0 means no limit. -->
    <MaxSubscriptionCancelAfterSnapshot>0</MaxSubscriptionCancelAfterSnapshot>
    <!-- Maximum allowed requests since last counters snapshot. 0 means no 
    limit. Must be consistent with other requests type limitations. -->
    <MaxRequestsAfterSnapshot>0</MaxRequestsAfterSnapshot>

    <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
    attached to the executing application domain.  -->
    <!-- Uncomment this to enable debug traces on first chance exceptions. 
    Use only for debugging purposes.  -->
    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>  -->

    <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
    attached to the executing application domain.  -->
    <!-- Uncomment this to enable debug traces on unhandled exceptions. 
    Use only for debugging purposes.  -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>  -->

    <!-- If set to "true" invalid cast first chance exceptions will not be 
    traced.  -->
    <!-- Uncomment this to disable debug tracing of invalid cast first 
    chance exceptions.  -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions>  -->

    <!-- If is "true" calls CoInitializeSecurity, which disables Schannel 
    COM authentication.  -->
    <IntitalizeCOMSecurity>false</IntitalizeCOMSecurity>

    <!-- Additional attributes that may be used are: Username, Password, 
    Domain, ProxyUri, AlwaysUseDA20, LicenseKey  -->
    <!-- UseDuplicates "true" or "false" indicates whether to duplicate 
    connection per request or to use locks. 
    This is used where is not possible to work without locks. At the end 
    of the request the connection is released.
    Prior to server license you can set maximum duplicates to be used 
    after which lock will be obtained. MaxDuplicates 0 means no restrictions.  -->
    <OpcConnection Url="opcda://localhost/Matrikon.OPC.Simulation" Enabled="true" Priority="1000"/>

    <!-- If you specify Read = "1" and Write = "2" that means when Read 
    operation is executing and at the same time come Write operation they 
    will be executed in parallel, 
    but if comes Read operation then the second Read operation will wait 
    until the first Read operation completes. If you specify Read="" that 
    means there is no locking
    on this operation and all request are executed simultaneously in 
    parallel. -->
    <SyncTokens Read="" Write="" Browse="" Subscribe="" 
    SubscriptionCancel="" GetProperties="" GetStatus=""></SyncTokens>

    <!-- Set the expected code page of incomming strings from OPC DA. -->
    <!-- <SourceCodePage>1252</SourceCodePage> -->
    <!-- Set the proper code page incomming string to be converted to. -->
    <!-- <DestinationCodePage>1251</DestinationCodePage> -->
  </OpcServer>
</PluginOpcDaConfiguration>
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

\[**OpcServer**\]

> **OPC DA** plugin module supports multiple connections to **OPC DA**
servers. Each connection is configured via a separate "**OpcServer**"
section.

## Configuring Connections

**OPC DA** plugin supports multiple connections to **OPC DA** servers.
Each connection is configured via a separate "**OpcServer**" section in
the plugin configuration file 
**&lt;InstallDir&gt;\\Plugins\\OpcDa\\Config\\Smart.OpcXml.Plugin.Configuration.xml**.

*__Example:__*

```xml
  <!-- Set Enabled to "true" if you have locally installed Matrikon OPC DA   simulation server -->
  <!-- RequestExecutionTimeout - The request execution timeout in 
  milliseconds after that the connection will be considered as broken. 
  Range [5000-180000] ms -->
  <!-- MaxLongRunningRequests - Maximum long running requests detected 
  after that the addin will be restarted. Minimum is 1. -->
  <!-- CheckConnectionStateInterval - Opc DA server connection check 
  interval in milliseconds. Range [3000 - 60000]ms -->
  <!-- ValidateItemsBeforeSubscribe - if true items will be validated 
  through group before adding to it. -->
  <!-- DA20ValidateItemsAfterBrowse - If is set "true" returned items from 
  browse will be validate. (DA20 only) -->
  <!-- DA20BrowseEnumeratorBlockSize - Specifies address space browse 
  enumerator how many items to fetch at once. (Range from 10 to 10000). (DA20 only) -->
  <!-- MTKN$LOCAL -->
  <OpcServer Enabled="false" CheckConnectionStateInterval="3000" 
  RequestExecutionTimeout="60000" MaxLongRunningRequests="1" 
  ValidateItemsBeforeSubscribe="true">
    <!-- NLog logger name. If empty or omitted the null logger will be used 
    instead.  -->
    <LoggerName>Smart.OpcXml.Plugins.OpcDa.AddIn.MTKN$LOCAL</LoggerName>
    <!-- Value indicating whether plugin supports browse.  -->
    <SupportBrowse>true</SupportBrowse>
    <!-- Value indicating whether plugin supports get properties  -->
    <SupportGetProperties>true</SupportGetProperties>
    <!-- Value indicating whether plugin supports read.  -->
    <SupportRead>true</SupportRead>
    <!-- Value indicating whether plugin supports write.  -->
    <SupportWrite>true</SupportWrite>
    <!-- Value indicating whether plugin supports subscribe.  -->
    <SupportSubscribe>true</SupportSubscribe>
    <!-- Value indicating whether plugin supports get status.  -->
    <SupportGetStatus>true</SupportGetStatus>
    <!-- Specifies if plugin module supports continuation points. If is set 
    to "true" address space permissions will not be applied on Browse response. -->
    <SupportsContinuationPoint>true</SupportsContinuationPoint>
    <!-- Plugin module alias.  -->
    <Alias>MTKN$LOCAL</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space 
    items path and name.  -->
    <PathSeparator>.</PathSeparator>
    <!-- Minimum requested sampling rate in milliseconds. Value cannot be 
    lower than 1000 ms.  -->
    <MinSubscriptionSamplingRate>1000</MinSubscriptionSamplingRate>
    <!-- Default requested sampling rate in milliseconds if such is not 
    specified. Value cannot be lower than 1000 ms.  -->
    <DefaultSubscriptionSamplingRate>3000</DefaultSubscriptionSamplingRate>
    <!-- Buffer size of each subscribe request item. Used when 
    EnableBuffering is specified in Subscribe. Cannot be lower than 2.  -->
    <MaxSubscriptionItemBufferSize>10</MaxSubscriptionItemBufferSize>
    <!-- Default SubscriptionPingRate in milliseconds if such is not 
    specified in Subscribe. Range [10 000;300 000] ms. -->
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <!-- The maximum subscribe lists. After reaching that value, the server 
    will not execute subscribes any more until
  total count of subscribed lists in the server becomes less than that 
  value. MaxSubscriptions cannot be lower than 10.  -->
    <MaxSubscriptions>1000</MaxSubscriptions>
    <!-- Maximum allowed number of items per subscribe list.Cannot be lower 
    than 50  -->
    <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
    <!-- Maximum allowed number of items per read list. 0 if no 
    restrictions -->
    <MaxItemsPerRead>0</MaxItemsPerRead>
    <!-- Maximum allowed number of items per write list. 0 if no 
    restrictions -->
    <MaxItemsPerWrite>0</MaxItemsPerWrite>
    <!-- Maximum allowed number of items per get properties list. 0 if no 
    restrictions -->
    <MaxItemsPerGetProperties>0</MaxItemsPerGetProperties>
    <!-- The maximum items returned per browse request. If value is greater 
    than 0, and MaxElementsReturned is 0 or greater than MaxItemsPerBrowse 
    it will be forced to this value. If 0 there is no constraint.
        SupportsContiunationPoint must be set to "true" in order the 
        restriction to be taken into account for this gateway. -->
    <MaxItemsPerBrowse>0</MaxItemsPerBrowse>

    <!-- Interval in milliseconds that subscriptions manager should check 
    for and clean expired subscriptions. CleanExpiredSubscriptionsInterval 
    cannot be lower than 1000ms.  -->
    <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
    <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be 
    greater than 50000 ms.  -->
    <MaxHoldTime>50000</MaxHoldTime>
    <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime 
    cannot be greater than 50000ms.  -->
    <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>

    <!-- Initial capacity of read buffer cache. Specify count of samples.  -->
    <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
    <!-- Maximum capacity of read buffer cache. Specify count of samples.  -->
    <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>

    <!-- Interval in milliseconds of estimating read buffer cache counters. 
    Value cannot be lower than 1000 ms.  -->
    <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>  

    <!-- Interval in milliseconds of estimating subscriptions manager 
    counters. Value cannot be lower than 1000 ms.  -->
    <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>  

    <!-- Interval in milliseconds of estimating performance counters. Value 
    cannot be lower than 1000 ms. -->
    <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>

    <!-- The following limitations are per estimation interval! -->
    <!-- Maximum allowed read requests since last counters snapshot. 0 
    means no limit. -->
    <MaxReadAfterSnapshot>0</MaxReadAfterSnapshot>
    <!-- Maximum allowed write requests since last counters snapshot. 0 
    means no limit. -->
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
    <!-- Maximum allowed get status requests since last counters snapshot. 
    0 means no limit. -->
    <MaxGetStatusAfterSnapshot>0</MaxGetStatusAfterSnapshot>
    <!-- Maximum allowed get properties requests since last counters 
    snapshot. 0 means no limit. -->
    <MaxGetPropertiesAfterSnapshot>0</MaxGetPropertiesAfterSnapshot>
    <!-- Maximum allowed subscription cancels since last counters snapshot. 
    0 means no limit. -->
    <MaxSubscriptionCancelAfterSnapshot>0</MaxSubscriptionCancelAfterSnapshot>
    <!-- Maximum allowed requests since last counters snapshot. 0 means no 
    limit. Must be consistent with other requests type limitations. -->
    <MaxRequestsAfterSnapshot>0</MaxRequestsAfterSnapshot>

    <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
    attached to the executing application domain.  -->
    <!-- Uncomment this to enable debug traces on first chance exceptions. 
    Use only for debugging purposes.  -->
    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>  -->

    <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
    attached to the executing application domain.  -->
    <!-- Uncomment this to enable debug traces on unhandled exceptions. Use 
    only for debugging purposes.  -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>  -->

    <!-- If set to "true" invalid cast first chance exceptions will not be 
    traced.  -->
    <!-- Uncomment this to disable debug tracing of invalid cast first 
    chance exceptions.  -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions>  -->

    <!-- If is "true" calls CoInitializeSecurity, which disables Schannel 
    COM authentication.  -->
    <IntitalizeCOMSecurity>false</IntitalizeCOMSecurity>

    <!-- Additional attributes that may be used are: Username, Password, 
    Domain, ProxyUri, AlwaysUseDA20, LicenseKey  -->
    <!-- UseDuplicates "true" or "false" indicates whether to duplicate 
    connection per request or to use locks. 
    This is used where is not possible to work without locks. At the end of 
    the request the connection is released.
    Prior to server license you can set maximum duplicates to be used after 
    which lock will be obtained. MaxDuplicates 0 means no restrictions.  -->
    <OpcConnection Url="opcda://localhost/Matrikon.OPC.Simulation" Enabled="true" Priority="1000"/>

    <!-- If you specify Read = "1" and Write = "2" that means when Read 
    operation is executing and at the same time come Write operation they 
    will be executed in parallel, 
    but if comes Read operation then the second Read operation will wait 
    until the first Read operation completes. If you specify Read="" that 
    means there is no locking
    on this operation and all request are executed simultaneously in 
    parallel. -->
    <SyncTokens Read="" Write="" Browse="" Subscribe="" 
    SubscriptionCancel="" GetProperties="" GetStatus=""></SyncTokens>

    <!-- Set the expected code page of incomming strings from OPC DA. -->
    <!-- <SourceCodePage>1252</SourceCodePage> -->
    <!-- Set the proper code page incomming string to be converted to. -->
    <!-- <DestinationCodePage>1251</DestinationCodePage> -->
  </OpcServer>
```

As you see most of the addin configuration parameters are the same like
these of the **OPC DA** plugin module, that's why we will explain here
only additional ones:

\[**DebugTraceIgnoreInvalidCastFirstChanceExceptions**\]

> If is set to "**true**" invalid cast exceptions will not be traced by
first chance exceptions handler.

> *``Remark:`` Use this feature only for debugging purposes. It does matter
only if "**DebugTraceFirstChanceExceptions"** is turned on by setting it
to "**true**".*

\[**IntitalizeCOMSecurity**\]

> If is "true" **CoInitializeSecurity** is called, which disables
**Schannel** **COM** authentication.

> *``Remark:`` Use this if the **Smart OPC XML Server** process is running
under credentials that do not have access to the classic **OPC DA**
Server. In this case you have to provide username and password for
connecting to the classic **OPC DA** server and
**InitializeCOMSecurity** must be turned on, to disable **Schannel**
**COM** authentication, thus the **OPC XML Server** process identity
will not be used for impersonating **DCOM** requests.*

\[**SupportsContinuationPoint**\]

> Specifies if plugin module supports continuation points.

> *``Remark:`` If is set to \"**true**\" address space permissions will not
be applied on **Browse** response.*

\[**Enabled**\]

> If is set to "**true**" the specified **OpcServer** is enabled,
otherwise is disabled;

\[**SyncTokens**\]

> Used as locking mechanism for **OPC DA** operations. If you specify
**Read** = "1" and **Write** = "2" that means when **Read**
operation is executing and at the same time come **Write** operation
they will be executed in parallel, but if comes **Read** operation then
the second **Read** operation will wait until the first **Read**
operation completes. If you specify **Read**="" that means there is no
locking on this operation and all request are executed simultaneously in
parallel.

\[**SourceCodePage**\]

> Sets the expected code page of incomming strings from **OPC DA**. Used
in very rare situations when **DCOM** server cannot properly translate
strings into proper code page. Usually is commented.

\[**DestinationCodePage**\]

> Set the proper code page incomming string to be converted to. Used in
very rare situations when **DCOM** server cannot properly translate
strings into proper code page. Usually is commented.

\[**CheckConnectionStateInterval**\]

> Interval in milliseconds for checking **OpcServer** connnection state.
Value cannot be lower than 3000 ms.

\[**RequestExecutionTimeout**\]

> The request execution timeout in milliseconds after that the connection
will be considered as broken. Range \[5000-180000\] ms.

\[**MaxLongRunningRequests**\]

> Maximum long running requests detected after that the addin will be
restarted. Minimum is 1.

\[**ValidateItemsBeforeSubscribe**\]

> If "**true**" items will be validated through group before adding to it.

\[**DA20ValidateItemsAfterBrowse**\]

> If "**true**" returned items from browse will be validated. (**DA20**
only)

\[**DA20BrowseEnumeratorBlockSize**\]

> Specifies address space browse enumerator how many items to fetch at
once. (Range from 10 to 10000). (**DA20** only).

\[**OpcConnection**\]

> The **OpcConnection** attribute is used to specify coonection enpoint to
the classic **OPC DA Server**. You can connect to **DCOM** server which
supports **OPC DA 2.0** or **OPC DA 3.0** protocol version.
You can specify several **OpcConnection** attributes and prioritize them
by using the "**Priority**" attribute of the **OpcConnection**. The
bigger values means higher prioriry. Specifying several
**OpcConnection** attributes is used for specifiying redundand
connection points or servers. If one connection becomes broken then the
others ordered by "**Priority**" will be tested to establish connection.

> Here are the attributes of **OpcConnection**:

>> ***Url*** - **OPC DA** Server endpoint address. The format is
"**opcda://computer name or ip address/DCOM service name or GUID**".
Enpoint address starts always with prefix "**opcda://**". After the
prefix you must point computer name (if you specify computer name,
remember that the name must be able to be translated to an **IP**
address, so check if the **DNS** will resolve it or if you don't use
**DNS** services, be sure to be specified in the computer hosts file) or
**IP** address. Finally you must point the **DCOM** service name or it's
**GUID**;

>> ***Enabled*** - If is set to "**true**" the specified **OpcConnection**
is enabled, otherwise is disabled;

>> ***Priority*** - Priority of the **OpcConnection**, higher values means
higher priority. When the current connection is broken the
**OpcConnections** with higher priorities will be tested first;

>> ***Username*** - Credential username for impersonating to the **OPC DA**
server (conisder turning on **InitializeCOMSecurity**);

>> ***Password*** - Credential password for impersonating to the **OPC DA**
server (conisder turning on **InitializeCOMSecurity**);

>> ***Domain*** - Credential domain for impersonating to the **OPC DA**
server (conisder turning on **InitializeCOMSecurity**);

>> ***ProxyUri*** - Specify a proxy address if your connection passes
through;

>> ***AlwaysUseDA20*** - Specifies if **OPC DA 2.0** to be used regardless
of that the **DCOM** server supports **OPC DA 3.0**;

>> ***LicesneKey*** - Put the licence key here if you have such for
connecting to the **OPC DA** server;

>> ***UseDiplicates*** - If is set to "**true**" and the protocol version is
**OPC DA 2.0** then when browsing the server address space, each user
will use a separate connection which is opened and closed after the
request finishes. Thus address space browsings are made concurrently in
other case users requests are executed consequently;

>> ***MaxDuplicates*** - Prior to server license you can set the maximum
number of duplicated connections to be used after exhausting it the
users browse requests will be executed consequently. 0 means no
restrictions.

*__Example:__*

```xml
<OpcServer Enabled="true" CheckConnectionStateInterval="3000" 
RequestExecutionTimeout="60000" MaxLongRunningRequests="1" 
ValidateItemsBeforeSubscribe="true" DA20ValidateItemsAfterBrowse="false" 
DA20BrowseEnumeratorBlockSize="1000">
    <LoggerName>Smart.OpcXml.Plugins.OpcDa.AddIn.SWP-EPKS-410</LoggerName>
    <SupportBrowse>true</SupportBrowse>
    <SupportGetProperties>true</SupportGetProperties>
    <SupportRead>true</SupportRead>
    <SupportWrite>true</SupportWrite>
    <SupportSubscribe>true</SupportSubscribe>
    <SupportGetStatus>true</SupportGetStatus>
    <SupportsContinuationPoint>true</SupportsContinuationPoint>
    <Alias>SWP-EPKS-410</Alias>
    <PathSeparator>.</PathSeparator>
    <OriginalPathSeparator>.</OriginalPathSeparator>
    <MinSubscriptionSamplingRate>1000</MinSubscriptionSamplingRate>
    <DefaultSubscriptionSamplingRate>3000</DefaultSubscriptionSamplingRate>
    <MaxSubscriptionItemBufferSize>10</MaxSubscriptionItemBufferSize>
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <MaxSubscriptions>1000</MaxSubscriptions>
    <MaxItemsPerSubscription>2000</MaxItemsPerSubscription>
    <MaxItemsPerRead>2000</MaxItemsPerRead>
    <MaxItemsPerWrite>1</MaxItemsPerWrite>
    <MaxItemsPerGetProperties>100</MaxItemsPerGetProperties>
    <MaxItemsPerBrowse>0</MaxItemsPerBrowse>
    <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
    <MaxHoldTime>50000</MaxHoldTime>
    <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>
    <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
    <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>
    <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>  
    <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>  
    <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>
    <MaxReadAfterSnapshot>0</MaxReadAfterSnapshot>
    <MaxWriteAfterSnapshot>0</MaxWriteAfterSnapshot>
    <MaxSubscribeAfterSnapshot>0</MaxSubscribeAfterSnapshot>
    <MaxPolledRefreshAfterSnapshot>0</MaxPolledRefreshAfterSnapshot>
    <MaxBrowseAfterSnapshot>0</MaxBrowseAfterSnapshot>
    <MaxGetStatusAfterSnapshot>0</MaxGetStatusAfterSnapshot>
    <MaxGetPropertiesAfterSnapshot>0</MaxGetPropertiesAfterSnapshot>
    <MaxSubscriptionCancelAfterSnapshot>0</MaxSubscriptionCancelAfterSnapshot>
    <MaxRequestsAfterSnapshot>0</MaxRequestsAfterSnapshot>
    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>  -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>  -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions>  -->
    <IntitalizeCOMSecurity>true</IntitalizeCOMSecurity>
    <OpcConnection Url="opcda://SWP-EPKS-410A/HWHsc.OPCServer" 
    Enabled="true" Priority="0" UseDuplicates="true" Username="user" 
    Password="pass"/>
    <OpcConnection Url="opcda://SWP-EPKS-410B/HWHsc.OPCServer" 
    Enabled="true" Priority="1000" UseDuplicates="true" Username="user" 
    Password="pass"/>  
    <SyncTokens Read="1" Write="1" Browse="" Subscribe="1" 
    SubscriptionCancel="1" GetProperties="1" GetStatus=""></SyncTokens>

    <!-- <SourceCodePage>1252</SourceCodePage> -->
    <!-- <DestinationCodePage>1251</DestinationCodePage> -->
  </OpcServer>
```

## AddIn Slots

Each enabled **OPC DA Server** configuration, described in **OpcServer**
sections, is raised in a separate addin process using managed add-in
framework. Because of technology constraint it is not possible to raise
two addin processes from the same place. That's the reason why we use
slots for each addin process. The number of available slots must be
greater or equal to the number enabled **OpcServer** configurations. In
other case some of the **OpcServer** configurations will remain down due
to lack of slots. The **Smart OPC XML Server OPC DA** plugin comes with
initially prepared 15 slots situated in

**&lt;InstallDir&gt;** - This is the base server folder. Here is situated
the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **OpcDa** - An **OPC XML DA/OPC DA** wrapper plugin module;

>>> **Bin** - Contains binaries of the plugin module;

>>> **AddIns** - Contains plugin module addins;

>>>> **Slot0** - Slot 0 of the Opc Server Addin;

>>>> **Slot1** - Slot 1 of the Opc Server Addin;

>>>> **... **

>>>> **Slot14** - Slot 14 of the Opc Server Addin;

You can increase available slots like creating a new folder (beneath
**AddIns** where the other slots are placed ) named for example
**Slot15** and copy all content of the **Slot0** folder into the new one
(**Slot15**).