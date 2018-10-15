**Smart OPC XML DA Gateway** plugin provides ability for cascade-linking
of **OPC XML DA Servers**.

## Directory Structure

**&lt;InstallDir&gt;** - This is the base server folder. Here is situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **Gateway** - An **OPC XML DA Gateway** plugin;

>>> **Bin** - Contains binaries of the plugin;

>>> **Config** - Contains configuration files of the plugin;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **Smart OPC XML DA Gateway** plugin configuration is separated in
several **XML** configuration files situated in
**&lt;InstallDir&gt;\\Plugins\\Gateway\\Config** folder. Configuration
attributes of the **Smart OPC XML DA Gateway** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\Gateway\\Config\\Smart.OpcXml.Plugin.Configuration.xml**
file.

*__Example:__*

```xml
<?xml version="1.0"?>
<PluginGatewayConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Gateway</LoggerName>
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
  <Alias>GATEWAY</Alias>
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
  subscribe request items for new values.
  DataRefreshInterval cannot be lower than 100ms. -->
  <DataRefreshInterval>1000</DataRefreshInterval>
  <!-- Interval in milliseconds that subscriptions manager should check for 
  and clean expired subscriptions.
  CleanExpiredSubscriptionsInterval cannot be lower than 1000ms. -->
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
  <!-- Maximum allowed read requests since last counters snapshot. 0 means no limit. -->
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
  <!-- Maximum allowed subscription cancels since last counters snapshot. 0 
  means no limit. -->
  <MaxSubscriptionCancelAfterSnapshot>0</MaxSubscriptionCancelAfterSnapshot>
  <!-- Maximum allowed requests since last counters snapshot. 0 means no 
  limit. Must be consistent with other requests type limitations.
   -->
  <MaxRequestsAfterSnapshot>0</MaxRequestsAfterSnapshot>

  <!-- 
      According to the XML spec, an XML processor is supposed to convert 
      all CR-LF pairs (and single CR’s) to a single LF.
      (see http://www.w3.org/TR/2000/REC-xml-20001006#sec-line-ends).
      
      2.11 End-of-Line Handling
      XML parsed entities are often stored in computer files which, for 
      editing convenience, are organized into lines. 
      These lines are typically separated by some combination of the 
      characters carriage-return (#xD) and line-feed (#xA).
      To simplify the tasks of applications, the characters passed to an 
      application by the XML processor must be as if 
      the XML processor normalized all line breaks in external parsed 
      entities (including the document entity) on input, 
      before parsing, by translating both the two-character sequence #xD 
      #xA and any #xD that is not followed by #xA to a single #xA character.
  
      NewLineHandling setting applies when writing text content or 
      attribute values. Each of the NewLineHandling values is described 
      below:
        Entitize - The Entitize setting tells the XmlWriter to replace new 
        line characters that would not be otherwise preserved by a 
        normalizing XmlReader with character entities. This is useful in 
        round-trip scenarios where the output is read by a normalizing 
        XmlReader. Additional normalization rules apply for attribute 
        values when round tripping since \t, \n and \r are replaced with a 
        space in attribute values when normalized in an XmlReader.

        Replace - The Replace setting tells the XmlWriter to replace new 
        line characters with \r\n, which is the new line format used by the 
        Microsoft Windows operating system. This helps to ensure that the 
        file can be correctly displayed by the Notepad or Microsoft Word 
        applications. This setting also replaces new lines in attributes 
        with character entities to preserve the characters. This is the 
        default value.

        None    - The None setting tells the XmlWriter to leave the input 
        unchanged. This setting is used when you not want any new-line 
        processing. This is useful when the output is read by an XmlReader 
        that does not do any normalization (for example, an XmlTextReader 
        with default settings.)
                  
      For more details about NewLineHadnling see 
      https://msdn.microsoft.com/en-us/library/system.xml.xmlwritersettings.newlinehandling%28v=vs.110%29.aspx 
  -->
  <soapNewLineHandlingExtension enable="true">
    <!-- Turns on entitizing of the request if any characters comes unentitized like '\r'. -->
    <inputProcessing enable="true">
      <xmlWriter newLineHandling="Entitize"></xmlWriter>
    </inputProcessing>

    <!-- Turns on entitizing of the response if any characters comes unentitized like '\r'. -->
    <outputProcessing enable="true">
      <xmlWriter newLineHandling="Entitize"></xmlWriter>
    </outputProcessing>
  </soapNewLineHandlingExtension>

  <!-- If is set to "true". DefaultFirstChanceExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on first chance exceptions. 
  Use only for debugging purposes.  -->
  <!-- 
  <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> 
  -->

  <!-- If is set to "true". DefaultUnhandledExceptionsHandler will be 
  attached to the executing application domain.  -->
  <!-- Uncomment this to enable debug traces on unhandled exceptions. Use 
  only for debugging purposes.  -->
  <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->
  
  <!-- UseDefaultAthentication is valid only for NTLM or Kerberos 
  authentication mechanisms. Not valid for others (e.g. Basic 
  authentication) -->
  <!-- CompressionType - possible values are "none", "decompress", "gzip" 
  or "deflate". Choose one of the available options. If omitted "none" will 
  be considered. -->
  <!-- CompressionType - none - disables compression. -->
  <!-- CompressionType - decompress - tells server what kind of 
  decompression algorithms support and if the server supports it then sends 
  responses with proper compression. -->
  <!-- CompressionType - gzip - forces gzip compression algorithm of the 
  requests and tells server that supports gzip decompression of responses. -->
  <!-- CompressionType - deflate - forces deflate compression algorithm of 
  the requests and tells server that supports gzip decompression of 
  responses. -->
  <!-- Remark: Duplex compression types gzip and deflate can work only with 
  Smart OPC XML Server and other specific servers which supports duplex 
  compression modes. -->
  <!-- UseChunkedTransfer - possible values are "true", "false". Choose one 
  of the available options. If omitted "false" will be considered. -->
  <!-- SupportsContiunationPoint - possible values are "true", "false". If 
  is "true" MaxElementsReturned will be passed to the gateway and 
  corresponding ContinuationPoint will be exchanged. If is "true" address 
  space permission will not be applied for this gateway.-->

   <Gateway Url="https://swp-dc-2/OpcXmlDa.asmx"
           Enabled="true"
           Alias="SSL_SWP-DC-2"
           PathSeparator="."
           OriginalPathSeparator="."
           UseAuthentication="true"
           PreAuthenticate="true"
           Username="mngr"
           Password="manager"
           UseDefaultCredentials="false"
           ClientCertificateHash="2B88177FD972EDCFF1610A035205E995B71B7B34"
           ServerCertificateHash="75D0FED71881F2141B5B6CB24801DFA554439B1C"
           CompressionType ="gzip"
           UseChunkedTransfer="false"
           SupportsContinuationPoint="true"
           MaxItemsPerSubscription="0"
           MaxItemsPerRead="0"
           MaxItemsPerWrite="0"
           MaxItemsPerGetProperties="0"
           MaxItemsPerBrowse="0"/> 

  
  <Gateway Url="http://swp-dc-2:9081/OpcXmlDa.asmx"
           Enabled="true"
           Alias="SWP-DC-2"
           PathSeparator="."
           OriginalPathSeparator="."
           UseAuthentication="true"
           PreAuthenticate="true"
           Username="mngr"
           Password="manager"
           UseDefaultCredentials="false"
           ClientCertificateHash=""
           ServerCertificateHash=""
           CompressionType ="gzip"
           UseChunkedTransfer="false"
           SupportsContinuationPoint="true"
           MaxItemsPerSubscription="0"
           MaxItemsPerRead="0"
           MaxItemsPerWrite="0"
           MaxItemsPerGetProperties="0"
           MaxItemsPerBrowse="0"/> 
  <Gateway Url="http://advosol.com/XMLDADemo/TS_Sim/OpcDAGateway.asmx" 
  Enabled="true" Alias="ADVOSOL_TS_SIM" PathSeparator="." 
  OriginalPathSeparator="." CompressionType ="decompress"/>
  <Gateway Url="http://advosol.com/XMLDADemo/XML_Sim/OpcXmlDaServer.asmx" 
  Enabled="true" Alias="ADVOSOL_XML_SIM" PathSeparator="." 
  OriginalPathSeparator="." CompressionType ="decompress"/>
  <Gateway Url="http://demo-opcxml.opclabs.com/XmlDaSampleServer/Service.asmx" 
  Enabled="true" Alias="OPCLABS" PathSeparator="." 
  OriginalPathSeparator="." CompressionType ="decompress"/>
</PluginGatewayConfiguration>
```
Here we will describe only additional configuration attributes, because
common ones are described above:

## **SOAP messages and New Line Handling**

According to the **XML** spec, an **XML** processor is supposed to
convert all **CR-LF** pairs (and single CR's) to a single LF (see
<http://www.w3.org/TR/2000/REC-xml-20001006#sec-line-ends>).

**XML** parsed entities are often stored in computer files which, for
editing convenience, are organized into lines. These lines are typically
separated by some combination of the characters carriage-return
(**\#xD**) and line-feed (**\#xA**). To simplify the tasks of
applications, the characters passed to an application by the **XML**
processor must be as if the **XML** processor normalized all line breaks
in external parsed entities (including the document entity) on input,
before parsing, by translating both the two-character sequence **\#xD**
**\#xA** and any **\#xD** that is not followed by **\#xA** to a single
**\#xA** character.

**NewLineHandling** setting applies when writing text content or
attribute values. Each of the **NewLineHandling** values is described
below:

**Entitize** - The **Entitize** setting tells the **XmlWriter** to
replace new line characters that would not be otherwise preserved by a
normalizing **XmlReader** with character entities. This is useful in
round-trip scenarios where the output is read by a normalizing
**XmlReader**. Additional normalization rules apply for attribute values
when round tripping since **\\t**, **\\n** and **\\r** are replaced with
a space in attribute values when normalized in an **XmlReader**.

**Replace** - The **Replace** setting tells the **XmlWriter** to replace
new line characters with **\\r\\n**, which is the new line format used
by the **Microsoft Windows** operating system. This helps to ensure that
the file can be correctly displayed by the **Notepad** or **Microsoft
Word** applications. This setting also replaces new lines in attributes
with character entities to preserve the characters. This is the default
value.

**None** - The **None** setting tells the **XmlWriter** to leave the
input unchanged. This setting is used when you not want any new-line
processing. This is useful when the output is read by an **XmlReader**
that does not do any normalization (for example, an **XmlTextReader**
with default settings.)

For more details about **NewLineHadnling** see:

<https://msdn.microsoft.com/en-us/library/system.xml.xmlwritersettings.newlinehandling%28v=vs.110%29.aspx>

For this purpose there is an extension named
**SoapNewLineHandlingExtension** which is used to handle new line
processings.

*__Example:__*

```xml
<soapNewLineHandlingExtension enable="true">
    <!-- Turns on entitizing of the request if any characters comes unentitized like '\r'. -->
    <inputProcessing enable="true">
      <xmlWriter newLineHandling="Entitize"></xmlWriter>
    </inputProcessing>

    <!-- Turns on entitizing of the response if any characters comes unentitized like '\r'. -->
    <outputProcessing enable="true">
      <xmlWriter newLineHandling="Entitize"></xmlWriter>
    </outputProcessing>
</soapNewLineHandlingExtension>
```

Extension consists of 2 part - **inputProcessing** and
**outputProcessing**. Enabling or disabling the entire extension is
controlled by the **enable** attribute (**true/false**) of the
**soapNewLineHandlingExtension** configuration tag. Enabling or
disabling a processing part is controlled by the **enable** attribute
(**true/false**) of the processing part configuration tag respectively
(**inputProcessing** or **outputProcessing**). The **newLineHandling**
attribute of the **xmlWriter** tag of each processing part determines
the way new lines are processed. The **inputProcessing** part is
presponsible for the incoming messages and the **outputProcessing** part
is responsible for the outgouing messages respectively.

## Configuring Connections

Gateway plugin supports multiple connections to different **OPC XML DA**
servers. Each connection is configured via a separate "**Gateway**"
section in the plugin configuration file
**&lt;InstallDir&gt;\\Plugins\\Gateway\\Config\\Smart.OpcXml.Plugin.Configuration.xml**.

*__Example:__*

```xml
<Gateway Url="https://swp-dc-2/OpcXmlDa.asmx"
           Enabled="true"
           Alias="SSL_SWP-DC-2"
           PathSeparator="."
           OriginalPathSeparator="."
           UseAuthentication="true"
           PreAuthenticate="true"
           Username="mngr"
           Password="manager"
           UseDefaultCredentials="false"
           ClientCertificateHash="2B88177FD972EDCFF1610A035205E995B71B7B34"
           ServerCertificateHash="75D0FED71881F2141B5B6CB24801DFA554439B1C"
           CompressionType ="gzip"
           UseChunkedTransfer="false"
           SupportsContinuationPoint="true"
           MaxItemsPerSubscription="0"
           MaxItemsPerRead="0"
           MaxItemsPerWrite="0"
           MaxItemsPerGetProperties="0"
           MaxItemsPerBrowse="0"/> 
```

\[**Url**\]

> The Uniform Resource Locator to the **OPC XML DA Server**.

\[**Enabled**\]Attribute

> If is set to "**true**", enales the specified gateway connection.

\[**PathSeparator**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

\[**OriginalPathSeparator**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

\[**UseAuthentication**\]

> Enables authentication if is set to "**true**".

\[**PreAuthenticate**\]

> If is set to "**true**" enables the pre-authentication.
Pre-authentication sends credentials with the request. Thus eliminates
sending requests twice.

\[**Username**\]

> Username for the authentication (if is enabled).

\[**Password**\]

> Password for the authentication (if is enabled);

\[**UseDefautlCredentials**\]

> If is set to true, service logon credentials will be used.

> *``Remark:`` Valid only for **NTLM** or **Kerberos** authentication
mechanisms. Not valid for others (e.g. **Basic** authentication).*

\[**ClientCertificateHash**\]

> Provide thumbprint of the client certificate to be used. If this gateway
is connecting to **Smart OPC XML Server** using **HTTPS** transport
protocol and server configuration parameter
"**ValidateClientCertificates**" is set to "**true**", then you must
provide client certificate hash. Otherwise leave it empty. This
certificate must be installed in the **Personal** certificate store of
**Local Machine**. When client certificate verification is performed,
this certificate hash must be also described in the server configuration
file, under section "**Configuration**", attribute
"**ClientCertificateHash**".

\[**ServerCertificateHash**\]
> Provide accepted server certificate thumbprint. If you want your
gateway to validate server certificate, then you must provide server
certificate thumbprint. If you leave this parameter empty, then
gateway will not validate server ssl certificate.

\[**CompressionType**\]

> Specifies if to or not to use compression mechanisms in the
communication. Possible values are "**none**", "**gzip**" or
"**deflate**". If omitted "**none**" will be considered and
compression will not be used.

\[**UseChunkedTransfer**\]

> Possible values are "**true**", "**false**". If omitted
"**false**" will be considered. If is set to "**true**", chunked
transfer encoding will be enabled.

\[**SupportsContinuationPoint**\]

> Possible values are "**true**", "**false**". If omitted
"**false**" will be considered. If is "**true**"
**MaxElementsReturned** will be passed to the gateway and corresponding
**ContinuationPoint** will be exchanged, but address space permission
will not be applied for this gateway.

\[**MaxItemsPerSubscription**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#Common Plugin's Configuration
Attributes), but refers to the specified connection.

\[**MaxItemsPerRead**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#Common Plugin's Configuration
Attributes), but refers to the specified connection.

\[**MaxItemsPerWrite**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

\[**MaxItemsPerGetProperties**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

\[**MaxItemsPerBrowse**\]

>  Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-da-module.md#common-plugins-configuration-attributes), but refers to the specified connection.