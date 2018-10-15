**Smart OPC XML DA WMI** plugin provides ability to read data through
the **Windows Management Instrumentation** interface.

## Directory Structure

**&lt;InstallDir&gt;** - This is the base server folder. Here is
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **Wmi** - An **OPC XML DA WMI** plugin;

>>> **Bin** - Contains binaries of the plugin;

>>> **Config** - Contains configuration files of the plugin;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **OPC XML DA WMI** plugin configuration is separated in several
**XML** configuration files situated in
**&lt;InstallDir&gt;\\Plugins\\Wmi\\Config** folder. Configuration
attributes of the **OPC XML DA WMI** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\Wmi\\Config\\Smart.OpcXml.Plugin.Configuration.xml**
file.

*__Example:__*

```xml
<?xml version="1.0"?>
<PluginWmiConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Wmi</LoggerName>
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
  <Alias>WMI</Alias>
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
  specified in Subscribe. Cannot be lower than 10000 ms. -->
  <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
  <!-- The maximum subscribe lists. After reaching that value, the server 
  will not execute subscribes any more until 
  total count of subscribed lists in the server becomes less than that 
  value. MaxSubscriptions cannot be lower than 10. -->
  <MaxSubscriptions>1000</MaxSubscriptions>
  <!-- Maximum allowed number of items per subscribe list.Cannot be lower than 50 -->
  <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
  <!-- Interval in milliseconds that subscriptions manager should check 
  subscribe request items for new values.
  DataRefreshInterval cannot be lower than 100ms. -->
  <DataRefreshInterval>1000</DataRefreshInterval>
  <!-- Interval in milliseconds that subscriptions manager should check 
  for and clean expired subscriptions.
  CleanExpiredSubscriptionsInterval cannot be lower than 1000ms. -->
  <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
  <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be greater than 50000 ms. -->
  <MaxHoldTime>50000</MaxHoldTime>
  <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime 
  cannot be greater than 50000ms. -->
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
  <!-- Interval in milliseconds of estimating performance counters. Value cannot be lower than 1000ms. -->
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
  <!-- Maximum allowed write requests since last counters snapshot. 0 means no limit. -->
  <MaxWriteAfterSnapshot>0</MaxWriteAfterSnapshot>
  <!-- Maximum allowed subscribe requests since last counters snapshot. 0 means no limit. -->
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
  <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on unhandled exceptions. Use 
  only for debugging purposes.  -->
  <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>

  <WmiConfiguration HostMachine="" Enabled="true">
    <!-- NLog logger name. If empty or omitted the null logger will be 
    used instead. -->
    <LoggerName>Smart.OpcXml.Plugins.Wmi.Local</LoggerName>
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
    <Alias>LOCAL</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space items path and name. -->
    <PathSeparator>.</PathSeparator>
    <!-- Plugin module OriginalPathSeparator used for the plugin address 
    space items path and name. Original path separator is replaced with 
    path separator. -->
    <OriginalPathSeparator>\</OriginalPathSeparator>
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
    specified in Subscribe. Cannot be lower than 10000 ms. -->
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <!-- The maximum subscribe lists. After reaching that value, the 
    server will not execute subscribes any more until 
    total count of subscribed lists in the server becomes less than that 
  value. MaxSubscriptions cannot be lower than 10. -->
    <MaxSubscriptions>1000</MaxSubscriptions>
    <!-- Maximum allowed number of items per subscribe list.Cannot be 
    lower than 50 -->
    <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
    <!-- Interval in milliseconds that subscriptions manager should check 
    subscibe request items for new values. 
    DataRefreshInterval cannot be lower than 100ms. -->
    <DataRefreshInterval>1000</DataRefreshInterval>
    <!-- Interval in milliseconds that subscriptions manager should check 
    for and clean expired subscriptions.
  CleanExpiredSubscriptionsInterval cannot be lower than 1000ms. -->
    <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
    <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be 
    greater than 50000 ms. -->
    <MaxHoldTime>50000</MaxHoldTime>
    <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime 
    cannot be greater than 50000ms. -->
    <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>
    <!-- How many subscriptions should be evaluated by one thread in 
    subscriptions manager. Value cannot be lower than 50. -->
    <EvaluatedSubscriptionsPerThread>400</EvaluatedSubscriptionsPerThread>
    <!-- Maximum items to be read  at once in order to refresh 
    subscriptions data by subscriptions manager. -->
    <MaxRefreshedItemsAtOnce>100</MaxRefreshedItemsAtOnce>
    <!-- Initial capacity of read buffer cache. Specify count of samples. -->
    <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
    <!-- Maximum capacity of read buffer cache. Specify count of samples. -->
    <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>
    <!-- Interval in milliseconds of estimating performance counters. 
    Value cannot be lower than 1000ms. -->
    <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>
    <!-- Interval in milliseconds of estimating read buffer cache 
    counters. Value cannot be lower than 1000ms. -->
    <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>
    <!-- Interval in milliseconds of estimating subscriptions manager 
    counters. Value cannot be lower than 1000ms. -->
    <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>

    <Username></Username>
    <Password></Password>
    <!-- Sets the COM authentication level to be used for operations in 
    this connection. -->
    <!--  Summary:
         Authentication level should remain as it was before.
    Unchanged = -1,
    
     Summary:
         The default COM authentication level. WMI uses the default Windows Authentication setting.
    Default = 0,
    
     Summary:
         No COM authentication.
    None = 1,
    
     Summary:
         Connect-level COM authentication.
    Connect = 2,
    
     Summary:
         Call-level COM authentication.
    Call = 3,
    
     Summary:
         Packet-level COM authentication.
    Packet = 4,
    
     Summary:
         Packet Integrity-level COM authentication.
    PacketIntegrity = 5,
    
     Summary:
         Packet Privacy-level COM authentication.
    PacketPrivacy = 6, -->
    <!-- <Authentication></Authentication> -->

    <!-- Authority to be used to authenticate the specified user. -->
    <!-- <Authority></Authority> -->

    <!--  Summary:
         Default impersonation.
    Default = 0,
    
     Summary:
         Anonymous COM impersonation level that hides the identity of the caller.
         Calls to WMI may fail with this impersonation level.
    Anonymous = 1,
    
     Summary:
         Identify-level COM impersonation level that allows objects to query the credentials
         of the caller. Calls to WMI may fail with this impersonation level.
    Identify = 2,
    
     Summary:
         Impersonate-level COM impersonation level that allows objects to use the
         credentials of the caller. This is the recommended impersonation level for
         WMI calls.
    Impersonate = 3,
    
     Summary:
         Delegate-level COM impersonation level that allows objects to permit other
         objects to use the credentials of the caller. This level, which will work
         with WMI calls but may constitute an unnecessary security risk, is supported
         only under Windows 2000.
    Delegate = 4, -->
    <!-- <Impersonation></Impersonation> -->

    <!-- Indicating whether user privileges need to be enabled
    for the connection operation. This property should only be used when the
    operation performed requires a certain user privilege to be enabled (for
    example, a machine restart). -->
    <!-- <EnablePrivileges></EnablePrivileges> -->

    <!-- Locale to be used for the connection operation. -->
    <!-- <Locale></Locale> -->

    <ScanRate>60000</ScanRate>

    <!-- AppDomain -->
    <WmiClass ClassPath="root\WebAdministration\AppDomain" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      <WmiClassMap Name="SmartWeb" Filter="SiteName='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- WorkerProcess -->
    <WmiClass ClassPath="root\WebAdministration\WorkerProcess" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      <WmiClassMap Name="SmartWeb" Filter="AppPoolName='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_ComputerSystem -->
    <WmiClass ClassPath="root\CIMV2\Win32_ComputerSystem" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_System -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_System" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="30000" QualifierSpecified="false" Enabled="true"/>
    </WmiClass>

    <!-- Win32_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_Processor" Enabled="true">
      <Description Value="CPU data" Enabled="true"/>
      <EngineeringUnits Value="CPU units" Enabled="true"/>

      <WmiProperty PropertyName="AddressWidth" Enabled ="true">
        <Description Value="Specifies address width of the processor." Enabled="true"/>
        <EngineeringUnits Value="bits" Enabled="true"/>
      </WmiProperty>
    </WmiClass>

    <!-- Win32_PerfRawData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfRawData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PhysicalMemory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PhysicalMemory" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <!-- <WmiClassMap Name="Bank0" Filter="SerialNumber='0D178300'" Enabled ="true"/>
      <WmiClassMap Name="Bank1" Filter="SerialNumber='0D378346'" Enabled ="true"/>
      <WmiClassMap Name="Bank2" Filter="SerialNumber='0D57834B'" Enabled ="true"/>
      <WmiClassMap Name="Bank3" Filter="SerialNumber='0D678301'" Enabled ="true"/> -->
    </WmiClass>

    <!-- Win32_PerfRawData_PerfOS_Memory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfRawData_PerfOS_Memory" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Memory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Memory" Enabled ="true">
      <!-- <EuType Value="" Qualifier="" QualifierSpecified="false" Enabled="false"/>
      <EuInfo Qualifier="" QualifierSpecified="false" Enabled="true">
        <Value>Open</Value>
        <Value>Close</Value>
        <Value>In Transit</Value>
      </EuInfo> -->
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <!-- <EngineeringUnits/>
      <OpenLabel/>
      <CloseLabel/>
      <HighEU/>
      <LowEU/>
      <HighIR/>
      <LowIR/>
      <MinimumValue/>
      <MaximumValue/>
      <ValuePrecision/> -->
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>

      <WmiProperty PropertyName="" Enabled ="true">
        <Description Value="" Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
        <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      </WmiProperty>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Cache -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Cache" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_W3SVC_WebService -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_W3SVC_WebService" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
      <WmiClassMap Name="SmartWeb" Filter="Name='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_W3SVC_WebServiceCache -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_W3SVC_WebServiceCache" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
      <WmiClassMap Name="SmartWeb" Filter="Name='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfProc_Process -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfProc_Process" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Idle" Filter="Name='Idle'" Enabled ="true"/>
      <WmiClassMap Name="OPCXMLSVC" Filter="Name='Smart.OpcXml.Service'" Enabled ="true"/>
      <WmiClassMap Name="AddIns" Filter="Name LIKE 'AddInProcess%'" Enabled ="true"/>
      <WmiClassMap Name="W3WP" Filter="Name LIKE 'w3wp%'" Enabled ="true"/>
    </WmiClass>

  </WmiConfiguration>

  <!--  Set Enabled to "true" if you want to connect to a remote machine. 
  Before that must be configured!  -->
  <WmiConfiguration HostMachine="SWP-WEB-2" Enabled="false">
    <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
    <LoggerName>Smart.OpcXml.Plugins.Wmi.SWP-WEB-2</LoggerName>
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
    <Alias>SWP-WEB-2</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space 
    items path and name. -->
    <PathSeparator>.</PathSeparator>
    <!-- Plugin module OriginalPathSeparator used for the plugin address 
    space items path and name. Original path separator is replaced with 
    path separator. -->
    <OriginalPathSeparator>\</OriginalPathSeparator>
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
    specified in Subscribe. Cannot be lower than 10000 ms. -->
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <!-- The maximum subscribe lists. After reaching that value, the 
    server will not execute subscribes any more until total count of 
    subscribed lists in the server becomes less than that value. 
    MaxSubscriptions cannot be lower than 10. -->
    <MaxSubscriptions>1000</MaxSubscriptions>
    <!-- Maximum allowed number of items per subscribe list.Cannot be 
    lower than 50 -->
    <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
    <!-- Interval in milliseconds that subscriptions manager should check 
    subscibe request items for new values. DataRefreshInterval cannot be 
    lower than 100ms. -->
    <DataRefreshInterval>1000</DataRefreshInterval>
    <!-- Interval in milliseconds that subscriptions manager should check 
    for and clean expired subscriptions. CleanExpiredSubscriptionsInterval 
    cannot be lower than 1000ms. -->
    <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
    <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be 
    greater than 50000 ms. -->
    <MaxHoldTime>50000</MaxHoldTime>
    <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime 
    cannot be greater than 50000ms. -->
    <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>
    <!-- How many subscriptions should be evaluated by one thread in 
    sunscriptions manager. Value cannot be lower than 50. -->
    <EvaluatedSubscriptionsPerThread>400</EvaluatedSubscriptionsPerThread>
    <!-- Maximum items to be read  at once in order to refresh 
    subscriptions data by subscriptions manager. -->
    <MaxRefreshedItemsAtOnce>100</MaxRefreshedItemsAtOnce>
    <!-- Initial capacity of read buffer cache. Specify count of samples. -->
    <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
    <!-- Maximum capacity of read buffer cache. Specify count of samples. -->
    <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>
    <!-- Interval in milliseconds of estimating performance counters. 
    Value cannot be lower than 1000ms. -->
    <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>
    <!-- Interval in milliseconds of estimating read buffer cache 
    counters. Value cannot be lower than 1000ms. -->
    <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>
    <!-- Interval in milliseconds of estimating subscriptions manager 
    counters. Value cannot be lower than 1000ms. -->
    <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>

    <Username>SWP-WEB-2\mngr</Username>
    <Password>manager</Password>
    <!-- Sets the COM authentication level to be used for operations in 
    this connection. -->
    <!--  Summary:
         Authentication level should remain as it was before.
    Unchanged = -1,
    
     Summary:
         The default COM authentication level. WMI uses the default Windows Authentication setting.
    Default = 0,
    
     Summary:
         No COM authentication.
    None = 1,
    
     Summary:
         Connect-level COM authentication.
    Connect = 2,
    
     Summary:
         Call-level COM authentication.
    Call = 3,
    
     Summary:
         Packet-level COM authentication.
    Packet = 4,
    
     Summary:
         Packet Integrity-level COM authentication.
    PacketIntegrity = 5,
    
     Summary:
         Packet Privacy-level COM authentication.
    PacketPrivacy = 6, -->
    <Authentication>PacketPrivacy</Authentication>
    <!-- Authority to be used to authenticate the specified user. -->
    <!-- <Authority></Authority> -->
    <!--  Summary:
         Default impersonation.
    Default = 0,
    
     Summary:
         Anonymous COM impersonation level that hides the identity of the caller.
         Calls to WMI may fail with this impersonation level.
    Anonymous = 1,
    
     Summary:
         Identify-level COM impersonation level that allows objects to query the credentials
         of the caller. Calls to WMI may fail with this impersonation level.
    Identify = 2,
    
     Summary:
         Impersonate-level COM impersonation level that allows objects to use the
         credentials of the caller. This is the recommended impersonation level for
         WMI calls.
    Impersonate = 3,
    
     Summary:
         Delegate-level COM impersonation level that allows objects to permit other
         objects to use the credentials of the caller. This level, which will work
         with WMI calls but may constitute an unnecessary security risk, is supported
         only under Windows 2000.
    Delegate = 4, -->
    <Impersonation>Impersonate</Impersonation>

    <!-- Indicating whether user privileges need to be enabled
    for the connection operation. This property should only be used when the
    operation performed requires a certain user privilege to be enabled (for
    example, a machine restart). -->
    <!-- <EnablePrivileges></EnablePrivileges> -->
    <!-- Locale to be used for the connection operation. -->
    <!-- <Locale></Locale> -->

    <ScanRate>60000</ScanRate>
    
    <!-- AppDomain -->
    <WmiClass ClassPath="root\WebAdministration\AppDomain" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      <WmiClassMap Name="SmartWeb" Filter="SiteName='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- WorkerProcess -->
    <WmiClass ClassPath="root\WebAdministration\WorkerProcess" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      <WmiClassMap Name="SmartWeb" Filter="AppPoolName='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_ComputerSystem -->
    <WmiClass ClassPath="root\CIMV2\Win32_ComputerSystem" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_System -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_System" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="30000" QualifierSpecified="false" Enabled="true"/>
    </WmiClass>

    <!-- Win32_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_Processor" Enabled="true">
      <Description Value="CPU data" Enabled="true"/>
      <EngineeringUnits Value="CPU units" Enabled="true"/>

      <WmiProperty PropertyName="AddressWidth" Enabled ="true">
        <Description Value="Specifies address width of the processor." Enabled="true"/>
        <EngineeringUnits Value="bits" Enabled="true"/>
      </WmiProperty>
    </WmiClass>

    <!-- Win32_PerfRawData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfRawData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PhysicalMemory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PhysicalMemory" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <!-- <WmiClassMap Name="Bank0" Filter="SerialNumber='0D178300'" Enabled ="true"/>
      <WmiClassMap Name="Bank1" Filter="SerialNumber='0D378346'" Enabled ="true"/>
      <WmiClassMap Name="Bank2" Filter="SerialNumber='0D57834B'" Enabled ="true"/>
      <WmiClassMap Name="Bank3" Filter="SerialNumber='0D678301'" Enabled ="true"/> -->
    </WmiClass>

    <!-- Win32_PerfRawData_PerfOS_Memory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfRawData_PerfOS_Memory" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Memory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Memory" Enabled ="true">
      <!-- <EuType Value="" Qualifier="" QualifierSpecified="false" Enabled="false"/>
      <EuInfo Qualifier="" QualifierSpecified="false" Enabled="true">
        <Value>Open</Value>
        <Value>Close</Value>
        <Value>In Transit</Value>
      </EuInfo> -->
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <!-- <EngineeringUnits/>
      <OpenLabel/>
      <CloseLabel/>
      <HighEU/>
      <LowEU/>
      <HighIR/>
      <LowIR/>
      <MinimumValue/>
      <MaximumValue/>
      <ValuePrecision/> -->
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>

      <WmiProperty PropertyName="" Enabled ="true">
        <Description Value="" Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
        <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      </WmiProperty>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Cache -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Cache" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_W3SVC_WebService -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_W3SVC_WebService" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
      <WmiClassMap Name="SmartWeb" Filter="Name='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_W3SVC_WebServiceCache -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_W3SVC_WebServiceCache" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
      <WmiClassMap Name="SmartWeb" Filter="Name='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfProc_Process -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfProc_Process" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Idle" Filter="Name='Idle'" Enabled ="true"/>
      <WmiClassMap Name="W3WP" Filter="Name LIKE 'w3wp%'" Enabled ="true"/>
    </WmiClass>
  </WmiConfiguration>
</PluginWmiConfiguration>
```

Here we will describe only additional configuration attributes, because
common ones are described above:

## Configuring WMI Connections

**WMI** plugin supports multiple connections to different machines. Each
connection is configured via a separate "**WmiConfiguration**" section
in the plugin configuration file
**&lt;InstallDir&gt;\\Plugins\\Wmi\\Config\\Smart.OpcXml.Plugin.Configuration.xml**.

*__Example:__*

```xml
<WmiConfiguration HostMachine="" Enabled="true">
    <!-- NLog logger name. If empty or omitted the null logger will be 
    used instead. -->
    <LoggerName>Smart.OpcXml.Plugins.Wmi.Local</LoggerName>
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
    <Alias>LOCAL</Alias>
    <!-- Plugin module pathSeparator used for the plugin address space 
    items path and name. -->
    <PathSeparator>.</PathSeparator>
    <!-- Plugin module OriginalPathSeparator used for the plugin address 
    space items path and name. Original path separator is replaced with 
    path separator. -->
    <OriginalPathSeparator>\</OriginalPathSeparator>
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
    specified in Subscribe. Cannot be lower than 10000 ms. -->
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <!-- The maximum subscribe lists. After reaching that value, the 
    server will not execute subscribes any more until total count of 
    subscribed lists in the server becomes less than that value. 
    MaxSubscriptions cannot be lower than 10. -->
    <MaxSubscriptions>1000</MaxSubscriptions>
    <!-- Maximum allowed number of items per subscribe list.Cannot be 
    lower than 50 -->
    <MaxItemsPerSubscription>300</MaxItemsPerSubscription>
    <!-- Interval in milliseconds that subscriptions manager should check 
    subscibe request items for new values. DataRefreshInterval cannot be 
    lower than 100ms. -->
    <DataRefreshInterval>1000</DataRefreshInterval>
    <!-- Interval in milliseconds that subscriptions manager should check 
    for and clean expired subscriptions. CleanExpiredSubscriptionsInterval 
    cannot be lower than 1000ms. -->
    <CleanExpiredSubscriptionsInterval>3000</CleanExpiredSubscriptionsInterval>
    <!-- The maximum HoldTime in milliseconds. MaxHoldTime cannot be 
    greater than 50000 ms. -->
    <MaxHoldTime>50000</MaxHoldTime>
    <!-- Maximum HoldTime+WaitTime in milliseconds. MaxHoldAndWaitTime 
    cannot be greater than 50000ms. -->
    <MaxHoldAndWaitTime>50000</MaxHoldAndWaitTime>
    <!-- How many subscriptions should be evaluated by one thread in 
    subscriptions manager. Value cannot be lower than 50. -->
    <EvaluatedSubscriptionsPerThread>400</EvaluatedSubscriptionsPerThread>
    <!-- Maximum items to be read  at once in order to refresh 
    subscriptions data by subscriptions manager. -->
    <MaxRefreshedItemsAtOnce>100</MaxRefreshedItemsAtOnce>
    <!-- Initial capacity of read buffer cache. Specify count of samples. -->
    <ReadBufferCacheInitialCapacity>1000</ReadBufferCacheInitialCapacity>
    <!-- Maximum capacity of read buffer cache. Specify count of samples. -->
    <ReadBufferCacheMaxSize>2000</ReadBufferCacheMaxSize>
    <!-- Interval in milliseconds of estimating performance counters. 
    Value cannot be lower than 1000ms. -->
    <PerformanceCountersEstimationInterval>60000</PerformanceCountersEstimationInterval>
    <!-- Interval in milliseconds of estimating read buffer cache 
    counters. Value cannot be lower than 1000ms. -->
    <ReadBufferCacheCountersEstimationInterval>60000</ReadBufferCacheCountersEstimationInterval>
    <!-- Interval in milliseconds of estimating subscriptions manager 
    counters. Value cannot be lower than 1000ms. -->
    <SubscriptionsManagerCountersEstimationInterval>60000</SubscriptionsManagerCountersEstimationInterval>

    <Username></Username>
    <Password></Password>
    <!-- Sets the COM authentication level to be used for operations in 
    this connection. -->
    <!--  Summary:
         Authentication level should remain as it was before.
    Unchanged = -1,
    
     Summary:
         The default COM authentication level. WMI uses the default Windows Authentication setting.
    Default = 0,
    
     Summary:
         No COM authentication.
    None = 1,
    
     Summary:
         Connect-level COM authentication.
    Connect = 2,
    
     Summary:
         Call-level COM authentication.
    Call = 3,
    
     Summary:
         Packet-level COM authentication.
    Packet = 4,
    
     Summary:
         Packet Integrity-level COM authentication.
    PacketIntegrity = 5,
    
     Summary:
         Packet Privacy-level COM authentication.
    PacketPrivacy = 6, -->
    <!-- <Authentication></Authentication> -->

    <!-- Authority to be used to authenticate the specified user. -->
    <!-- <Authority></Authority> -->

    <!--  Summary:
         Default impersonation.
    Default = 0,
    
     Summary:
         Anonymous COM impersonation level that hides the identity of the caller.
         Calls to WMI may fail with this impersonation level.
    Anonymous = 1,
    
     Summary:
         Identify-level COM impersonation level that allows objects to query the credentials
         of the caller. Calls to WMI may fail with this impersonation level.
    Identify = 2,
    
     Summary:
         Impersonate-level COM impersonation level that allows objects to use the
         credentials of the caller. This is the recommended impersonation level for
         WMI calls.
    Impersonate = 3,
    
     Summary:
         Delegate-level COM impersonation level that allows objects to permit other
         objects to use the credentials of the caller. This level, which will work
         with WMI calls but may constitute an unnecessary security risk, is supported
         only under Windows 2000.
    Delegate = 4, -->
    <!-- <Impersonation></Impersonation> -->

    <!-- Indicating whether user privileges need to be enabled
    for the connection operation. This property should only be used when the
    operation performed requires a certain user privilege to be enabled (for
    example, a machine restart). -->
    <!-- <EnablePrivileges></EnablePrivileges> -->

    <!-- Locale to be used for the connection operation. -->
    <!-- <Locale></Locale> -->

    <ScanRate>60000</ScanRate>

    <!-- AppDomain -->
    <WmiClass ClassPath="root\WebAdministration\AppDomain" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      <WmiClassMap Name="SmartWeb" Filter="SiteName='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- WorkerProcess -->
    <WmiClass ClassPath="root\WebAdministration\WorkerProcess" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      <WmiClassMap Name="SmartWeb" Filter="AppPoolName='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_ComputerSystem -->
    <WmiClass ClassPath="root\CIMV2\Win32_ComputerSystem" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_System -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_System" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <ScanRate Value ="30000" QualifierSpecified="false" Enabled="true"/>
    </WmiClass>

    <!-- Win32_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_Processor" Enabled="true">
      <Description Value="CPU data" Enabled="true"/>
      <EngineeringUnits Value="CPU units" Enabled="true"/>

      <WmiProperty PropertyName="AddressWidth" Enabled ="true">
        <Description Value="Specifies address width of the processor." Enabled="true"/>
        <EngineeringUnits Value="bits" Enabled="true"/>
      </WmiProperty>
    </WmiClass>

    <!-- Win32_PerfRawData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfRawData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PhysicalMemory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PhysicalMemory" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <!-- <WmiClassMap Name="Bank0" Filter="SerialNumber='0D178300'" Enabled ="true"/>
      <WmiClassMap Name="Bank1" Filter="SerialNumber='0D378346'" Enabled ="true"/>
      <WmiClassMap Name="Bank2" Filter="SerialNumber='0D57834B'" Enabled ="true"/>
      <WmiClassMap Name="Bank3" Filter="SerialNumber='0D678301'" Enabled ="true"/> -->
    </WmiClass>

    <!-- Win32_PerfRawData_PerfOS_Memory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfRawData_PerfOS_Memory" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Memory -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Memory" Enabled ="true">
      <!-- <EuType Value="" Qualifier="" QualifierSpecified="false" Enabled="false"/>
      <EuInfo Qualifier="" QualifierSpecified="false" Enabled="true">
        <Value>Open</Value>
        <Value>Close</Value>
        <Value>In Transit</Value>
      </EuInfo> -->
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <!-- <EngineeringUnits/>
      <OpenLabel/>
      <CloseLabel/>
      <HighEU/>
      <LowEU/>
      <HighIR/>
      <LowIR/>
      <MinimumValue/>
      <MaximumValue/>
      <ValuePrecision/> -->
      <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>

      <WmiProperty PropertyName="" Enabled ="true">
        <Description Value="" Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
        <ScanRate Value ="60000" QualifierSpecified="false" Enabled="true"/>
      </WmiProperty>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Cache -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Cache" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_W3SVC_WebService -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_W3SVC_WebService" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
      <WmiClassMap Name="SmartWeb" Filter="Name='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_W3SVC_WebServiceCache -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_W3SVC_WebServiceCache" Enabled ="true">
      <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
      <WmiClassMap Name="SmartWeb" Filter="Name='SmartWeb'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfOS_Processor -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_Processor" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Total" Filter="Name='_Total'" Enabled ="true"/>
    </WmiClass>

    <!-- Win32_PerfFormattedData_PerfProc_Process -->
    <WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfProc_Process" Enabled ="true">
      <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
      <WmiClassMap Name="Idle" Filter="Name='Idle'" Enabled ="true"/>
      <WmiClassMap Name="OPCXMLSVC" Filter="Name='Smart.OpcXml.Service'" Enabled ="true"/>
      <WmiClassMap Name="AddIns" Filter="Name LIKE 'AddInProcess%'" Enabled ="true"/>
      <WmiClassMap Name="W3WP" Filter="Name LIKE 'w3wp%'" Enabled ="true"/>
    </WmiClass>
  </WmiConfiguration>
```

Part of the configartion attributes are like common configuration
attributes, so we will discuss additional ones only:

*``Remark:`` **OriginalPathSeparator** is "**\\**" and it is recommended
"**PathSeparator**" to be seto to "**.**".*

\[**HostMachine**\]

> The name of the host machine you want connect to. Leave it empty for the
local machine.

\[**Enabled**\]

> If it is set to "**true**", the connection will be enabled.

\[**Username**\]

> Provide username to be used when connectiong to the machine or leave it
empty to use service logon credentials instead. If you are connecting to
remote machine, the user name must be prefixed with the machine name
like "SWP-WEB-2\\mngr". The same rule is valid when a domain is used.

\[**Password**\]

> Provide password to be used when connectiong to the machine or leave it
empty to use service logon credentials instead.

\[**Authentication**\]

> Sets the **COM** authentication level to be used for operations in this
connection.

> Possible values are:

> -   **Unchanged = -1** - Authentication level should remain as it was
    before;

> -   **Default = 0** - The default COM authentication level. WMI uses the
    default Windows Authentication setting;

> -   **None = 1** - No COM authentication;

> -   **Connect = 2** - Connect-level COM authentication;

> -   **Call = 3** - Call-level COM authentication;

> -   **Packet = 4** - Packet-level COM authentication;

> -   **PacketIntegrity = 5** - Packet Integrity-level COM authentication;

> -   **PacketPrivacy = 6** - Packet Privacy-level COM authentication;

> *``Remark:`` When you are connecting to remote machine
"**PacketPrivacy**" must be used. You may omit this attribute for local
connections.*

\[**Authority**\]

> Authority to be used to authenticate the specified user.

> *``Remark:`` Usually you may omit this attribute.*

\[**EnablePrivileges**\]

> If is set to "**true**" - user privileges will be enabled for the
connection operation. This property should only be used when the
operation performed requires a certain user privilege to be enabled (for
example, a machine restart).

*``Remark:`` Usually you may omit this attribute.*

\[**Impersonation**\]

> Defines which impersonation level to use.

> Possible values are:

> -   **Default = 0** - Default impersonation;

> -   **Anonymous = 1** - Anonymous COM impersonation level that hides the
    identity of the caller. Calls to WMI may fail with this
    impersonation level;

> -   **Identify = 2** - Identify-level COM impersonation level that
    allows objects to query the credentials of the caller. Calls to WMI
    may fail with this impersonation level;

> -   **Impersonate = 3** - Impersonate-level COM impersonation level that
    allows objects to use the credentials of the caller. This is the
    recommended impersonation level for WMI calls;

> -   **Delegate = 4** - Delegate-level COM impersonation level that
    allows objects to permit other objects to use the credentials of the
    caller. This level, which will work with WMI calls but may
    constitute an unnecessary security risk, is supported only under
    Windows 2000;

> *``Remark:`` When you are connecting to remote machine "**Impersonate**"
must be used. You may omit this attribute for local connections.*

\[**Locale**\]

> Locale to be used for the connection operation.

> *``Remark:`` Usually you may omit this attribute.*

\[**ScanRate**\]

> Specifies the default scan rate item property in milliseconds. Usually
is 60000 ms (1 minute).

## WMI Class Configuration

The **WMI** classes are represented like branches in the **OPC XML DA**
address space. **WMI** classes contains properties, which are
represented like **OPC XML DA** child items of the branch. You can make
additional configuarion to the specific **WMI** class. Thus you can
customize how **OPC XML DA** item properties of the class properties are
retrieved. Let see the following example:

```xml
<!-- Win32_PerfFormattedData_PerfOS_System -->
<WmiClass ClassPath="root\CIMV2\Win32_PerfFormattedData_PerfOS_System" Enabled ="true">
  <Description Qualifier="DisplayName" QualifierSpecified="true" Enabled="true"/>
  <ScanRate Value ="30000" QualifierSpecified="false" Enabled="true"/>
</WmiClass>
```

-   **ClassPath** -- the full **WMI** path to the class that we want to
    customize;

-   **Enabled** -- true/false, defines if the **WMI** class
    configuration is enabled;

Inside the "**WmiClass**" tag we can specify any set of standard **OPC
XML DA** item properties like **EngineeringUnits**, **MinimumValue**,
**MaximumValue**, **ValuePrecision** etc. (see for more information
**OPC XML DA 1.01 Sepcification**).

As we see from the example above there are two properties configured -
**Description** and **ScanRate**.

Each configured property has the following available attributes:

-   **Value** -- Provides a static value for the property;

-   **Qualifier** -- Defines name of property qualifier which will be
    used to retrieve the **OPC XML DA** item property value;

-   **QualifierSpecified** --"**true**"/"**false**", indicates if the
    specified property qualifier is used;

-   **Enabled** - "**true**"/"**false**", indicates if the property
    configuration is enabled or not;

The first property configuration "**Description**" defines that the
value will be retrieved via the property qualifier with name
"**DisplayName**". The second property configuration "**ScanRate**"
specifies that the value is constant "**30000**" and qualifiers will not
be used. Thus each class property which belongs to
**Win32\_PerfFormattedData\_PerfOS\_System** class if there is no
additional configuration at property level will return value "**30000**"
for **OPC XML DA** item property "**ScanRate**" and will try to fetch
value for the "**Description**" **OPC XML DA** item property from the
class property qualifier named "**DisplayName**".

## WMI Property Mapping

The **WMI** class properties are represented like items in the **OPC XML
DA** address space. **WMI** property mapping feature provides ability to
add or override specific **OPC XML DA** item properties of the **WMI**
class property. This can be done by adding "**WmiProperty**" tag inside
the "**WmiClass**" configuration tag.

*__Example:__*

```xml
<!-- Win32_Processor -->
<WmiClass ClassPath="root\CIMV2\Win32_Processor" Enabled="true">
   <Description Value="CPU data" Enabled="true"/>
   <EngineeringUnits Value="CPU units" Enabled="true"/>

   <WmiProperty PropertyName="AddressWidth" Enabled ="true">
     <Description Value="Specifies address width of the processor." Enabled="true"/>
     <EngineeringUnits Value="bits" Enabled="true"/>
   </WmiProperty>
 </WmiClass>
```

-   **PropertyName** - determines which property applies the
    configuration;

-   **Enabled** - "**true**"/"**false**", indicates if the property
    configuration is enabled or not;

Inside the "**WmiProperty**" tag we can specify any set of standard
**OPC XML DA** item properties like **EngineeringUnits**,
**MinimumValue**, **MaximumValue**, **ValuePrecision** etc. (see for
more information **OPC XML DA 1.01 Sepcification**).

As we see from the example above there are two properties configured -
**Description** and **EngineeringUnits**.

Each configured property has the following available attributes:

-   **Value** - Provides a static value for the property;

-   **Qualifier** - Defines name of property qualifier which will be
    used to retrieve the OPC XML DA item property value;

-   **QualifierSpecified** - "**true**"/"**false**", indicates if the
    specified property qualifier is used;

-   **Enabled** - "**true**"/"**false**", indicates if the property
    configuration is enabled or not;

Both property configurations "**Description**" and
"**EngineeringUnits**" defines that they static values.

## WMI Class Mapping

Each **WMI** class may have one or more available instances. For example
the class **Win32\_PhysicalMemory** has different instances for each
memory bank which differs by the class property "**SerialNumber**". If
we see investigate this class in the **OPC XML DA** address space we
will find that if we retrieve the item value of the **OPC XML DA** item
"**SerialNumber**", the value is array of strings containing the serial
numbers of the installed memory sticks in the machine. Imagine that we
want to remap each instance for the memory stick in separate branch in
the **OPC XML DA** server address space. We can do that by using **WMI**
class mapping feature.

*__Example:__*

```xml
<!-- Win32_PhysicalMemory -->
<WmiClass ClassPath="root\CIMV2\Win32_PhysicalMemory" Enabled ="true">
    <Description Qualifier="Description" QualifierSpecified="true" Enabled="true"/>
    <WmiClassMap Name="Bank0" Filter="SerialNumber='0D178300'" Enabled ="true"/>
    <WmiClassMap Name="Bank1" Filter="SerialNumber='0D378346'" Enabled ="true"/>
    <WmiClassMap Name="Bank2" Filter="SerialNumber='0D57834B'" Enabled ="true"/>
    <WmiClassMap Name="Bank3" Filter="SerialNumber='0D678301'" Enabled ="true"/> 
</WmiClass>
```

We define a **WMI** class mapping by adding a "**WmiClassMap**" tag
inside the "**WmiClass**" configuration tag, like show above.

The "**WmiClassMap**" has the following attributes:

-   **Name** - specifies the unique name of the map, for that class;

-   **Filter** - here we specify a filter which is applied to the
    **WQL** query before to be executed;

-   **Enabled** - "**true**" **/ "false"**, determines if the described
    map is enabled or not;

In result of the example above if we browse the **OPC XML DA** server
address space we will see that except the
**WMI.LOCAL.ROOT.CIMV2.Win32\_PhysicalMemory** branch we additional four
branched named respectively
**WMI.LOCAL.ROOT.CIMV2.Win32\_PhysicalMemory(Bank0)**,
**WMI.LOCAL.ROOT.CIMV2.Win32\_PhysicalMemory(Bank1)**,
**WMI.LOCAL.ROOT.CIMV2.Win32\_PhysicalMemory(Bank2)** and
**WMI.LOCAL.ROOT.CIMV2.Win32\_PhysicalMemory(Bank3)**.

The difference is that the
**WMI.LOCAL.ROOT.CIMV2.Win32\_PhysicalMemory** represents and returns
data for all memory banks, but the other 4 mapped classes returns data
only for the specified by the filter memory bank.