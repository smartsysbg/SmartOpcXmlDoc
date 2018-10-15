By default **Smart OPC XML Server** service is running under **Local System** account. If you change the account, you must assure the following:

The service account must have write access to the 
`C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Temporary ASP.NET Files` folder. You can assign the service account to the **IIS\_IUSRS** group which already has;

The service account must be able to start **HttpListerner** at specified url. You have to execute the following command for example (chage the **url** and **user** with the appropriate ones):

```cmd
netsh http add urlacl url=https://+:9443/ user=Everyone listen=yes
```

The service account must have write access to the entire service installation folder (e.g. `C:\Program Files\Smartsys Ltd\Smart OPC XML Server`);

If you use **HTTPS**, you have to grant access to the private key of the server certificate to the service account using **Windows HTTP Services Certificate Configuration Tool (WinHttpCertCfg.exe)**. You can download it from [here](https://www.microsoft.com/en-us/download/details.aspx?id=19801). You have to run the following command as example: 

```cmd
C:\Program Files (x86)\Windows Resource Kits\Tools\WinHttpCertCfg.exe -g -c LOCAL_MACHINE\MY -s "SmartWebSite" -a "SmartWebViewOnly";
```

Where the **SmartWebSite** is the common name of the certificate and **SmartWebViewOnly** is the service account name for example;

Open the **Web.config** file in the root service installation folder (e.g.
`C:\Program Files\Smartsys Ltd\Smart OPC XML Server\Web.config`), locate the following:

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
   <probing privatePath="Lib" />
</assemblyBinding>
```
and change the `privatePath="Lib"` to `privatePath="Lib;Bin"`

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
   <probing privatePath="Lib;Bin" />
</assemblyBinding>
```

Thus required libraries will be found when starting up.

*``Remark:`` This is needed if ASP .NET libraries are not installed.*