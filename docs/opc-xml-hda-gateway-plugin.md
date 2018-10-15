**Smart OPC XML HDA Gateway** plugin provides ability for cascade-linking of **OPC XML HDA Servers**.

## Directory Structure

**&lt;InstallDir&gt;** - This is the base server folder. Here is 
situated the starting executable of the server;

> **Plugins** - Here are situated server plugin modules;

>> **HdaGateway** - An **OPC XML HDA Gateway** plugin;

>>> **Bin** - Contains binaries of the plugin;

>>> **Config** - Contains configuration files of the plugin;

>>> **Logs** - Contains log files of the plugin;

## Configuration Attributes

The **Smart OPC XML HDA Gateway** plugin configuration is separated in
several **XML** configuration files situated in
**&lt;InstallDir&gt;\\Plugins\\HdaGateway\\Config** folder. Configuration
attributes of the **Smart OPC XML HDA Gateway** plugin are located in
**&lt;InstallDir&gt;\\Plugins\\HdaGateway\\Config\\Smart.OpcXml.HdaPlugin.Configuration.xml**
file.

__Example:__

```xml
<?xml version="1.0"?>
<HdaPluginGatewayConfiguration xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!-- NLog logger name. If empty or omitted the null logger will be used instead. -->
  <LoggerName>Smart.OpcXml.Plugins.Hda.HdaGateway</LoggerName>
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
  <Alias>GATEWAY</Alias>
  <!-- Plugin module pathSeparator used for the plugin address space items path and name. -->
  <PathSeparator>.</PathSeparator>
  <!-- Plugin module OriginalPathSeparator used for the plugin address space 
  items path and name. Original path separator is replaced with path separator. -->
  <OriginalPathSeparator>.</OriginalPathSeparator>
  <!-- Maximum available items to read at once via HdaReadAtTime. 0 means no 
  restriction. -->
  <MaxItemsPerHdaReadAtTime>0</MaxItemsPerHdaReadAtTime>
  <!-- Maximum available items to read at once via HdaReadProcessed. 0 means no 
  restriction. -->
  <MaxItemsPerHdaReadProcessed>0</MaxItemsPerHdaReadProcessed>
  <!-- Maximum available items to read at once via HdaReadRaw. 0 means no restriction. -->
  <MaxItemsPerHdaReadRaw>0</MaxItemsPerHdaReadRaw>
  <!-- Interval in milliseconds of estimating HDA performance counters. Value cannot be lower than 1000ms. -->
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
  <!-- 
      According to the XML spec, an XML processor is supposed to convert all 
      CR-LF pairs (and single CR’s) to a single LF.
      (see http://www.w3.org/TR/2000/REC-xml-20001006#sec-line-ends).
      
      2.11 End-of-Line Handling
      XML parsed entities are often stored in computer files which, for editing 
      convenience, are organized into lines. 
      These lines are typically separated by some combination of the characters 
      carriage-return (#xD) and line-feed (#xA).
      To simplify the tasks of applications, the characters passed to an 
      application by the XML processor must be as if 
      the XML processor normalized all line breaks in external parsed entities 
      (including the document entity) on input, 
      before parsing, by translating both the two-character sequence #xD #xA and 
      any #xD that is not followed by #xA to a single #xA character.
  
      NewLineHandling setting applies when writing text content or attribute 
      values. Each of the NewLineHandling values is described below:
        Entitize - The Entitize setting tells the XmlWriter to replace new line 
        characters that would not be otherwise preserved by a normalizing XmlReader 
                   with character entities. This is useful in round-trip 
                   scenarios where the output is read by a normalizing XmlReader. 
                   Additional normalization rules apply for attribute values when 
                   round tripping since \t, \n and \r are replaced with a space 
                   in attribute values 
                   when normalized in an XmlReader.

        Replace - The Replace setting tells the XmlWriter to replace new line 
        characters with \r\n, which is the new line format used by the 
                  Microsoft Windows operating system. This helps to ensure that 
                  the file can be correctly displayed by the Notepad or Microsoft 
                  Word applications. 
                  This setting also replaces new lines in attributes with 
                  character entities to preserve the characters. This is the 
                  default value.

        None    - The None setting tells the XmlWriter to leave the input 
        unchanged. This setting is used when you not want any new-line 
        processing. 
                  This is useful when the output is read by an XmlReader that 
                  does not do any normalization (for example, an XmlTextReader 
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
  
  <!-- UseDefaultAthentication is valid only for NTLM or Kerberos authentication 
  mechanisms. Not valid for others (e.g. Basic authentication) -->
  <!-- CompressionType - possible values are "none", "decompress", "gzip" or 
  "deflate". Choose one of the available options. If omitted "none" will be 
  considered. -->
  <!-- CompressionType - none - disables compression. -->
  <!-- CompressionType - decompress - tells server what kind of decompression 
  algorithms support and if the server supports it then sends responses with 
  proper compression. -->
  <!-- CompressionType - gzip - forces gzip compression algorithm of the requests 
  and tells server that supports gzip decompression of responses. -->
  <!-- CompressionType - deflate - forces deflate compression algorithm of the 
  requests and tells server that supports gzip decompression of responses. -->
  <!-- Remark: Duplex compression types gzip and deflate can work only with Smart 
  OPC XML Server and other specific servers which supports duplex compression 
  modes. -->
  <!-- UseChunkedTransfer - possible values are "true", "false". Choose one of 
  the available options. If omitted "false" will be considered. -->
  <!-- MaxItemsPerHdaReadAtTime - maximum available items to read at once via 
  HdaReadAtTime. 0 means no restriction. -->
  <!-- MaxItemsPerHdaReadProcessed - maximum available items to read at once via 
  HdaReadProcessed. 0 means no restriction. -->
  <!-- MaxItemsPerHdaReadRaw - maximum available items to read at once via 
  HdaReadRaw. 0 means no restriction. -->

  <HdaGateway Url="https://swp-dc-2/OpcXmlHda.asmx" 
              Enabled="true" 
              Alias="SWP-DC-2" 
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
              MaxItemsPerHdaReadAtTime="0"
              MaxItemsPerHdaReadProcessed="0"
              MaxItemsPerHdaReadRaw="0"/> 
			  
  <HdaGateway Url="http://swp-dc-2:9081/OpcXmlHda.asmx" 
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
              MaxItemsPerHdaReadAtTime="0"
              MaxItemsPerHdaReadProcessed="0"
              MaxItemsPerHdaReadRaw="0"/>			  
</HdaPluginGatewayConfiguration >
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

For more details about **NewLineHadnling** see [here](https://msdn.microsoft.com/en-us/library/system.xml.xmlwritersettings.newlinehandling%28v=vs.110%29.aspx)

For this purpose there is an extension named
**SoapNewLineHandlingExtension** which is used to handle new line
processings.

__Example:__

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

## Configuring connections

**HDA** Gateway plugin supports multiple connections to different **OPC
XML HDA** servers. Each connection is configured via a separate
"**HdaGateway**" section in the plugin configuration file
**&lt;InstallDir&gt;\\Plugins\\HdaGateway\\Config\\Smart.OpcXml.HdaPlugin.Configuration.xml**.

__Example:__

```xml
<HdaGateway Url="https://swp-dc-2/OpcXmlHda.asmx" 
              Enabled="true" 
              Alias="SWP-DC-2" 
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
              MaxItemsPerHdaReadAtTime="0"
              MaxItemsPerHdaReadProcessed="0"
              MaxItemsPerHdaReadRaw="0"/> 
```

\[**Url**\]

> The Uniform Resource Locator to the **OPC XML HDA Server**.

\[**Enabled**\]

> If is set to "**true**", enales the specified gateway connection.

\[**PathSeparator**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](#common-plugins-configuration-attributes-1), but refers to
the specified connection.

\[**OriginalPathSeparator**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-hda-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

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
file, under section "**Configuration**", attribute "**ClientCertificateHash**".

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

\[**MaxItemsPerHdaReadAtTime**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-hda-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

\[**MaxItemsPerHdaReadProcessed**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-hda-module.md#common-plugins-configuration-attributes), but refers to the specified connection.

\[**MaxItemsPerHdaReadRaw**\]

> Has the same meaning like in [Common Plugin's Configuration
Attributes](opc-xml-hda-module.md#common-plugins-configuration-attributes), but refers to the specified connection.