# Directory Structure

**&lt;InstallDir&gt;** - This is the installation folder. Here is the starting executable of the server;  
> **Bin** - Contains server's specific binaries;  
> **Config** - A folder containing configuration files of the server;  
> **Lib** - Common libraries. Contains a set of shared libraries used by the server and plugins;  
>> **Config** - A folder containing configuration files of the server's Power Shell management module;  

> **Logs** - Log files of the server;  
> **Plugins** - Here are situated server plugin modules;  
>> **Gateway** - **OPC XML DA** gateway plugin;  
>> **HdaGateway** - **OPC XML HDA** gateway plugin;  
>> **HdaVirtualize** - **OPC XML HDA** virtual items plugin;  
>> **OpcDa** - An **OPC XML DA/OPC DA** wrapper plugin;  
>> **OpcHda** - An **OPC XML HDA/OPC HDA** wrapper plugin;  
>> **Simulation** - **OPC XML DA** simulation plugin;  
>> **Virtualize** - **OPC XML DA** virtual items plugin;  
>> **Wmi** - **OPC XML DA/WMI** wrapper plugin;  

Usually each plugin consist of 3 subfolders:

> **Bin** - Contains binaries of the plugin;  
> **Config** - Contains configuration files of the plugin;  
> **Logs** - Contains log files of the plugin;  


# Configuration Files

Configuration of the server is separated in several **XML**
configuration files situated in "**&lt;InstallDir&gt;\Config**" folder:

* **Smart.OpcXml.AddressSpace.Elements.xml** - Describes browse elements
visible in the server's address space;

* **Smart.OpcXml.AddressSpace.ItemProperties.xml** - Regarding **OPC XML
DA** specification, each browse element item has properties, which are
described in this file;

*__`Remark:`__ Items, which exists in the **XML** configuration above, but
does not have properties described here, will not be loaded in the
server's address space.*

* **Smart.OpcXml.AddressSpace.Permissions.xml** - Contains permissions
over the server's address space, which parts of it are visible and which
not;

* **Smart.OpcXml.Hda.HdaServer.Configuration.xml** - Contains
configuration for the **OPC XML HDA** module of the server;

* **Smart.OpcXml.Server.Configuration.xml** - Contains configuration for
the **OPC XML DA** module of the server;

* **Smart.OpcXml.Service.Configuration.xml** - Contains configuration for the server startup;

# HTTP Listener

The **HTTP** listener configuration is situated in  
"**&lt;InstallDir&gt;\Config\Smart.OpcXml.Service.Configuration.xml**".

## HTTP Listener Prefixes

The **HTTP** listener prefixes describe on which **IP** addresses and
ports the listener should listen. The following example demonstrates
that the listener will listen on all binded addresses on port **9081**
for **HTTP** scheme and on port **9443** for **HTTPS** scheme:

*__Example:__*
```xml
<HttpListenerPrefixes>
    <string>http://+:9081/</string>
    <string>https://+:9443/</string>
</HttpListenerPrefixes>
```

An **URI** prefix string is composed of a scheme (**http** or
**https**), a host, an optional port, and an optional path. An example
of a complete prefix string is
"**http://www.contoso.com:8080/customerData/**". Prefixes must end in
a forward slash ("**/**").

When a port is specified, the host element can be replaced with
"**\***" to indicate that the **HTTP** listener accepts requests sent
to the port if the requested **URI** does not match any other prefix.
For example, to receive all requests sent to port **8080** when the
requested **URI** is not handled by any **HTTP** listener, the prefix is
"**http://\*:8080/**". Similarly, to specify that the **HTTP**
Listener accepts all requests sent to a port, replace the host element
with the "**+**" character, "**https://+:8080**". The "**\***" and
"**+**" characters can be present in prefixes that include paths.

*__`Remark:`__
For using **HTTPS** scheme you must provide a server
certificate. How to configure the **SSL** will be discussed later.*

By default server listens on **HTTP** port **9081**
(<http://localhost:9081/OpcXmlDa.asmx>, <http://localhost:9081/OpcXmlHda.asmx>).

# Tcp Client Channel Socket Cache Timeout

An integer that specifies the time, in seconds, after which a socket is
removed from the cache maintained by a **TcpClientChannel** object. The
default is five seconds. If value is negative or omitted, the defaul
five seconds will be used. Max allowed value is 60 seconds. If you
specify more than 60 seconds, timeout will be limited to 60 seconds. Do
not set it to 0 if you don't know exactly what are you doing! If you
plan to enable or change this value, and you plant to use remoting,
revise also **Smart.OpcXml.Plugin.Configuration.xml** configuration
files of the **OpcXmlDa** and **OpcXmlHda** plugins and change
**AddInProcessRestartWaitTime** with the appropriate value.

***Example:***
```xml
<TcpClientChannelSocketCacheTimeout>5</TcpClientChannelSocketCacheTimeout>
```

# HTTP Listener Threads

You can specify how many threads should be listening for requests at the
same time. If you specify 0, the **HTTP** listener will not be run (this
is useful when you don't want to start own listener, instead of that you
will use **IIS** to process requests).

*__Example:__*
```xml
<HttpListenerThreads>16</HttpListenerThreads>
```

*__`Remark:`__ Increasing too much listener threads may cause performance
degradation.*

# HTTP Request Queue Length

Specifies the maximum queued requests when there are no avaialble
threads to handle it. After reaching the maximum queued requests, each
next request will be rejected by the server. If value is 0 or negative
number, defaults will be used (1000).

*__Example:__*
```xml
<HttpRequestQueueLength>1</HttpRequestQueueLength>
```

# HTTP Authentication Schemes

The **HTTP** listener supports different authentication schemes like
**Digest**, **Negotiate**, **NTLM**, **Integrated Windows
Authentication**, **Basic** and **Anonymous**. By default authentication
is set to **Anonymous**. The following example demonstrates how the
**HTTP** listener can be configured for using **Integrated Windows
Authentication**.

*__Example:__*
```xml
<HttpListenerAuthenticationScheme>IntegratedWindowsAuthentication</HttpListenerAuthenticationScheme>
```

The other available authentication options are:

> **None** - No authentication is allowed. A client requesting a
**System.Net.HttpListener** object with this flag set will always
receive a **403 Forbidden** status. Use this flag when a resource should
never be served to a client;

> **Digest** - Specifies digest authentication;

> **Negotiate** - Negotiates with the client to determine the
authentication scheme. If both client and server support **Kerberos**,
it is used; otherwise, **NTLM** is used.

> **Ntlm** - Specifies **NTLM** authentication;

> **IntegratedWindowsAuthentication** - Specifies **Windows**
authentication;

> **Basic** - Specifies **basic** authentication;

> **Anonymous** - Specifies anonymous authentication.

# Client Certificates Validation

As mentioned above **HTTP** listener supports **SSL** connections. You
can specify **HTTP** listener to validate client certificate thumbprints
(hashes). To enable the thumbprint validation do the following:

Enable validate client certificate by setting "**true**" of the "**ValidateClientCertificates**" tag.

*__Example:__*
```xml
<ValidateClientCertificates>true</ValidateClientCertificates>
```

Describe valid certificates thumbprints by filling the "**ClientCertificateHashes**" tag.

*__Example:__*
```xml
<ClientCertificateHashes>
    <string>2B88177FD972EDCFF1610A035205E995B71B7B34</string>
    <string>75D0FED71881F2141B5B6CB24801DFA554439B1C</string>
</ClientCertificateHashes>
```

Use only capital letters without any separators between bytes (e.g.
**06C02C429B09473061B20225D592D4D4844F8F6A**).

# HTTP Compression

If "**HttpCompressionModule**" is added in the
"**&lt;InstallDir&gt;\\Web.config**" file and
"**HttpCompressionModuleEnableCompression**" is set to "**true**", in
the "**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.Service.Configuration.xml**"
configuration file, then compression of response will be enabled if the
the request has the appropriate "**Accept-Encoding**" header.
Supported commpression types are "**gzip**" and "**deflate**". If it is
"**false**" and http module is added, then only decompression will be
made if it is necessary.

Compression module configuration in the "**&lt;InstallDir&gt;\\Web.config**"
file:
```xml
<system.web>
    <httpModules>
        <!--Comment this if you want to disable compression. Supported commpression are gzip and deflate.-->
        <add name="HttpCompressionModule" type="Smart.OpcXml.Web.Modules.HttpCompressionModule"/>
    </httpModules>
</system.web>
```

# Chunked Transfer Encoding

**Chunked Transfer Encoding** is a data transfer mechanism in version
1.1 of the [Hypertext Transfer Protocol](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)
(**HTTP**) in which data is sent in a series of "**chunks**". It uses the 
[Transfer-Encoding](http://en.wikipedia.org/wiki/List_of_HTTP_header_fields#transfer-encoding-response-header)
**HTTP** header in place of the
[Content-Length](http://en.wikipedia.org/wiki/Content-Length) header,
which the earlier version of the protocol would otherwise
require [\[1\]](http://en.wikipedia.org/wiki/Chunked_transfer_encoding#cite_note-1).
Because the Content-Length header is not used, the sender does not need
to know the length of the content before it starts transmitting a
response to the receiver. Senders can begin transmitting
dynamically-generated content before knowing the total size of that
content.

If you want to use chunked transfer then set option
"**UseChunkedTransfer**" in the  
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.Service.Configuration.xml**"
configuration file to "**true**".

More information about "**Chunked Transfer Encoding**" you can find
[here](http://en.wikipedia.org/wiki/Chunked_transfer_encoding).

# Server Certificate Binding

To configure the **HTTP** listener **SSL** you must have a valid server
certificate. How to create one for demo purposes will be explained later
in appendices part. To configure used server certificate we use the
"**netsh**" command like:

```cmd
netsh http add sslcert ipport=0.0.0.0:9443 appid={6a6fe14a-e41d-42bd-9829-09a52c00ff86} certhash=75d0fed71881f2141b5b6cb24801dfa554439b1c clientcertnegotiation=enable
```

With "**ipport=0.0.0.0:9443**" we specify on all available addresses on
port **9443**.  
With "**appid={6a6fe14a-e41d-42bd-9829-09a52c00ff86}**"
we specify our application **ID**, which in this case is the application
**ID** of our startup binary which is
"**&lt;InstallDir&gt;\\Smart.OpcXml.Service.exe**". The application **ID**
is also known as the application **GUID**, which is almost unique. With
"**certhash=75d0fed71881f2141b5b6cb24801dfa554439b1c**" we describe the
thumbprint of the server certificate, which to be used. With
"**clientcertnegotiation=enable**" we specify that the server will ask
the client for its certificate in order to validate the thumbprint. The
parameter "**clientcertnegotiation=enable"** will allows C/S mutually
authentication based on certificates, i.e. server side could verify the
certificate validation of the client side as well as the client side
verifying the server side. If you don't want verification for client
side, just omit the parameter

*``Remark:`` The server certificate must be trusted by the machine and
must be installed in  
"**Local Computer\\Personal**" certificate store in order to work.*

To view the **SSL** certificate bindings you can use the command:

```cmd
netsh http show sslcert
```

The output should be something like:
```cmd
SSL Certificate bindings:
-------------------------
IP:port : 0.0.0.0:90
Certificate Hash : 75d0fed71881f2141b5b6cb24801dfa554439b1c
Application ID : {00000000-0000-0000-0000-000000000000}
Certificate Store Name : MY
Verify Client Certificate Revocation : Disabled
Verify Revocation Using Cached Client Certificate Only : Disabled
Usage Check : Enabled
Revocation Freshness Time : 0
URL Retrieval Timeout : 0
Ctl Identifier : (null)
Ctl Store Name : (null)
DS Mapper Usage : Disabled
Negotiate Client Certificate : Enabled
IP:port : 0.0.0.0:9443
Certificate Hash : 75d0fed71881f2141b5b6cb24801dfa554439b1c
Application ID : {6a6fe14a-e41d-42bd-9829-09a52c00ff86}
Certificate Store Name : (null)
Verify Client Certificate Revocation : Enabled
Verify Revocation Using Cached Client Certificate Only : Disabled
Usage Check : Enabled
Revocation Freshness Time : 0
URL Retrieval Timeout : 0
Ctl Identifier : (null)
Ctl Store Name : (null)
DS Mapper Usage : Disabled
Negotiate Client Certificate : Enabled
```

To delete SSL certificate binding you can use the command:

```cmd
netsh http delete sslcert ipport=0.0.0.0:9443
```

You can read more about **netsh** command line utility
[here](http://technet.microsoft.com/en-us/library/cc785383(v=ws.10).aspx).

*``Remark:`` If you want a non-privileged account to run the server, you
have to add **ACL** (**Access Control Lists**) to the system:*

*__Example:__*
```cmd
netsh http add urlacl url=https://+:9443/ user=DOMAIN\\user
```

Pay attention to the parameter "**user**". Put whatever user you want to
assign the start server right to here. If set the parameter
**user=users**, it will grant all user account (non-privileged) to start
the app and listen on the specific **IP** address and port.

# User Authentication and Authorization

As we mentioned above the **HTTP** listener accepts client requests and
transfers them to the **OPC XML DA** and **OPC XML HDA** Web services
via the **ASP .NET** runtime engine. **HTTP** listener must provide
identity for the **ASP .NET** application to make the authorization.
Thus authorization is made in the **ASP .NET** engine, that's why the
configuration is in the application **Web.config** file located in
"**&lt;InstallDir&gt;\\Web.config**".

So we make authentication and authorization as regular **ASP .NET**
application in the **&lt;system.web&gt;** part of the **ASP .NET** application **Web.config**.

*__Example:__*

```xml
<authentication mode= "Windows"></authentication>
<identity impersonate="true"/>
<authorization>
    <allow users=".\mngr, .\hawk" />
    <deny users="*" />
</authorization>
```

With setting authentication mode to "**Windows**", we say that we will
use the operating system users and roles for authentication and
authorization. In the authorization section, the allow subsection must
be always before deny one if exists. You can specify users or roles
(e.g. allow roles="**Administrators**", deny roles="**Users**"). As
specified in the example above all users are denied except "**mngr**"
and "**hawk**". More information about authentication element in
**Web.config** you can find
[here](http://msdn.microsoft.com/en-us/library/532aee0e(v=vs.85).aspx),
and for the authorization element
[here](http://msdn.microsoft.com/en-us/library/8d82143t(v=vs.85).aspx).

*``Remark:`` If **Web.config** is broken the **HTTP** listener won't
start.*

By default this section in commented in the **Web.config** file.

# SOAP Messages and New Line Handling

According to the **XML** spec, an **XML** processor is supposed to
convert all **CR-LF** pairs (and single CR's) to a single LF (see
[here](http://www.w3.org/TR/2000/REC-xml-20001006#sec-line-ends)).

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

For more details about **NewLineHadnling** see [here](https://msdn.microsoft.com/en-us/library/system.xml.xmlwritersettings.newlinehandling%28v=vs.110%29.aspx).

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

Extension's configuration section (**soapNewLineHandlingExtension**) is
located in the **Web.config** file. The configuration consists of 2
parts - **inputProcessing** and **outputProcessing**. Enabling or
disabling the entire extension is controlled by the **enable** attribute
(**true/false**) of the **soapNewLineHandlingExtension** configuration
tag. Enabling or disabling a processing part is controlled by the
**enable** attribute (**true/false**) of the processing part
configuration tag respectively (**inputProcessing** or
**outputProcessing**). The **newLineHandling** attribute of the
**xmlWriter** tag of each processing part determines the way new lines
are processed. The **inputProcessing** part is presponsible for the
incoming messages and the **outputProcessing** part is responsible for
the outgouing messages respectively.

# Process Model

The Process Model is part of the **ASP .NET** settings schema and is
configured via the application **Web.config** file located in
"**&lt;InstallDir&gt;\\Web.config**".

*__Example:__*

```xml
<processModel autoConfig="true" maxWorkerThreads="32" maxIoThreads="32" minWorkerThreads="16" minIoThreads="16"/>
```
Process model attributes:

\[**autoConfig**\]

Specifies whether to automatically configure the following settings to achieve optimal performance based on the machine configuration:

The **maxWorkerThreads** attribute.

The **maxIoThreads** attribute.

The **minFreeThreads** attribute of [**httpRuntime**](http://msdn.microsoft.com/en-us/library/e1f13641(v=vs.100).aspx)
element.

The **minLocalRequestFreeThreads** attribute of the
[**httpRuntime**](http://msdn.microsoft.com/en-us/library/e1f13641(v=vs.100).aspx)
element.

The **maxConnection** attribute of the [**&lt;connectionManagement&gt;**
(Network Settings)](http://msdn.microsoft.com/en-us/library/fb6y0fyc(v=vs.100).aspx)
element.

The values are set according to the **KB** article at
[**http://support.microsoft.com/?id=821268**](http://support.microsoft.com/?id=821268).

This attribute does not affect the **.NET Framework** client applications;
only **ASP.NET** applications.

The **autoConfig** attribute can be one of the following values:

* **True** - Indicates that **ASP.NET** automatically configures the attributes in the preceding list to achieve optimal performance based on the machine
configuration.

* **False** - Indicates that **ASP.NET** should use the explicitly defined values for the attributes in the preceding list.

The default in the **Machine.config** file is **True**, unless there is
a previously existing configuration.

\[**maxWorkerThreads**\]

Configures the maximum amount of worker threads to use for the process
on a per-CPU basis. For example, if this value is 25 on a
single-processor server, ASP.NET uses the runtime APIs to set the
process limit to 25. On a two-processor server, the limit is set to 50.
The value of this attribute must be equal to or greater than the
**minFreeThread** attribute setting in the [**httpRuntime**](http://msdn.microsoft.com/en-us/library/e1f13641(v=vs.100).aspx) configuration section. 
For information about threading types, see "**Threading Explained**" in [Improving ASP.NET Performance](http://go.microsoft.com/fwlink/?LinkId=43900). 

The range for this attribute is from **5** through **100**. The default is **20**.

\[**maxIoThreads**\]

Configures the maximum number of I/O threads to use for the process on a
per-CPU basis. For example, if this value is 25 on a single-processor
server, ASP.NET uses the runtime APIs to set the process limit to 25. On
a two-processor server, the limit is set to 50. The value of this
attribute must be equal to or greater than the **minFreeThread**
attribute setting in the
[**httpRuntime**](http://msdn.microsoft.com/en-us/library/e1f13641(v=vs.100).aspx) configuration section.
For information about threading types, see "**Threading Explained**"
in [Improving ASP.NET Performance](http://go.microsoft.com/fwlink/?LinkId=43900).

The range for this attribute is from **5** through **100**.
The default is **20**.

\[**minIoThreads**\]

Configures the minimum number of I/O threads to use for the process on a
per-CPU basis. Also see **maxIoThreads**.
For information about threading types, see "**Threading Explained**"
in [Improving ASP.NET Performance](http://go.microsoft.com/fwlink/?LinkId=43900).

The default is **1**.

More information about **Process Model** attributes you can find
[here](http://msdn.microsoft.com/en-us/library/7w2sway1(v=vs.100).aspx).

*``Remark:`` The Process Model element from **ASP .NET** Settings Schema
by default is not defined into the application **Web.config** file. If
you are not satisfied from the performance then you can configure it
globally using the **Machine.config** or for the specific application
locally using the application **Web.config** file, but before to do that
you have to allow local modifications of the **processModel** element by
changing the **allowDefinition** from "**MachineOnly**" to
"**MachineToApplication**".*

*__Example:__*

```xml
<section name="processModel"
type="System.Web.Configuration.ProcessModelSection, System.Web,
Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
allowDefinition="MachineToApplication" allowLocation="false" />
```

**Machine.config** is located here:

For x86 platform: 

**%SytemDrive%:\\Windows\\Microsoft.NET\\Framework\\\[version\]\\config\\machine.config**

For x64 platform:     

**%SystemDrive%:\\Windows\\Microsoft.NET\\Framework64\\\[version\]\\config\\machine.config**

It's recommended to omit this section from the **Web.config** file and
to leave the engine automatically to find the best configuration for
itself.

# Configuring the Remoting Services

The **HTTP** listener is responsible to accept client requests and
transfer them to the **OPC XML DA** and **OPC XML HDA** Web services.
Both **Web** services are respectively connected to the **OPC XML DA**
and **OPC XML HDA** modules through remoting proxies or directly.
Remoting proxies are needed only if you plan to run web services via
**IIS**. Configuration of the remoting proxies is situated in the same
**XML** file as the configuration of the **HTTP** listener
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.Service.Configuration.xml**".

To configure them you have to specify several things:

**EnableRemoting** - Set to "**true**" if you want to enable the
remoting proxies. Then you must use respectively **OpcXmlDaRem.asmx**
and **OpcXmlHdaRem.asmx** web services to access the server. If it is
"**false**", you must use **OpcXmlDa.asmx** and **OpcXmlHda.asmx** web
service only.

**RemotingServiceName** - Must be unique for the entire machine;

**RemotingServicePort** - Must be unique for the entire machine (if
**TCP** channel type is used, for **IPC** channel type also must be
unique, but it is used in different aspect, to create the unique port
name of the IPC channel);

**RemotingChannelType** - Recommended to use **TCP**.

*__Example:__*

```xml
<EnableRemoting>true</EnableRemoting>
<RemotingServiceName>Smart_OpcXml_BaseServerProxy</RemotingServiceName>
<RemotingServicePort>35101</RemotingServicePort\>
<RemotingChannelType>Tcp</RemotingChannelType\>
<HdaRemotingServiceName>Smart_OpcXml_BaseHdaServerProxy</HdaRemotingServiceName>
<HdaRemotingServicePort>35102</HdaRemotingServicePort>
<HdaRemotingChannelType>Tcp</HdaRemotingChannelType>
```

There are 2 different kinds of channels you can use:

**Tcp** - The recommended one;

**Ipc** - You can still use **IPC** channels, but if you do that, you
will lose the power shell server management features, which we will
discuss later, when you want remotely to control the server, because the
power shell management module uses the same remoting services for
management, but **IPC** channels are not visible for the remote
connected users unlike the **TCP** channels.

Briefly just use **TCP** channels if you want to use power shell server
management features. By default remoting is tured off.

# Debugging

For debugging purposes there are additional two options, in the
"**&lt;InstallDir&gt;\\Config\\Smart.OpcXml.Service.Configuration.xml**"
configuration file, which can help insvestigating unusual application
behavior.

If you set "**DebugTraceFirstChanceExceptions"** to "**true**", then an
event handler will be attached to the application domain first chance
exceptions handler and all exceptions will be traced to the log.

*__Example:__*

```xml
<DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions>
```

If you set "**DebugTraceUnhandledExceptions"** to "**true**", then an
event handler will be attached to the application domain unhandled
exceptions handler and all unhandled exceptions will be traced to the
log. Also in the log will be traced if the exception is terminating or
not.

*__Example:__*

```xml
<DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions>
```

If you set "**HttpServerDebugTraceFirstChanceExceptions"** to
"**true**", then an event handler will be attached to the executing
application domain of the **HttpServer** and all exceptions will be
traced to the log.

*__Example:__*

```xml
<HttpServerDebugTraceFirstChanceExceptions>true</HttpServerDebugTraceFirstChanceExceptions>
```

If you set "**HttpServerDebugTraceUnhandledExceptions"** to "**true**",
then an event handler will be attached to the executing application
domain of the **HttpServer** and all unhandled exceptions will be traced
to the log. Also in the log will be traced if the exception is
terminating or not.

*__Example:__*

```xml
<HttpServerDebugTraceUnhandledExceptions>true</HttpServerDebugTraceUnhandledExceptions>
```

*``Remark:`` Be careful when use these options, the log files can grow
dramatically if you leave them turned on. Use only for debugging
purposes.*