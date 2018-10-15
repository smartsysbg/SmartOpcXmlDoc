---
title: Стартиране на Smart OPC XML Server услугата под не-административен акаунт
---

По подразбиране **Smart OPC XML Server** услугата работи под **Local System** акаунта. Ако смените акаунта, трябва да имате в предвид
следното:

* Сървис акаунта трябва да има достъп за запис в директория  
"**C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\Temporary ASP.NET Files**". На акаунта може да му присвоите група **IIS\_IUSRS**,
която вече има достъп за запис;

* Сървис акаунта трябва да може да стартира **HTTP** лисънъра на 
зададения адрес. За целта трабва да се изпълни следната команда
(променете **url** и **user** със съответните такива):

```cmd
netsh http add urlacl url=http://+:9081/ user=Everyone listen=yes
```

* Сървис акаунта трябва да има достъп за запис до (напр.  
"**C:\\Program Files\\Smartsys Ltd\\Smart OPC XML Server**");

* Ако използвате **HTTPS** схема, сървис акаунта трябва да има достъп
до частния ключ на използвания сертификат, като използвате примерно
**Windows HTTP Services Certificate Configuration Tool (WinHttpCertCfg.exe)**. Може да изтеглите инструмента от [тук](**https://www.microsoft.com/en-us/download/details.aspx?id=19801**).
Трябва да изпълните следната команда:  

```cmd
C:\Program Files (x86)\Windows Resource Kits\Tools\WinHttpCertCfg.exe -g -c
LOCAL_MACHINE\MY -s "SmartWebSite" -a "SmartWebViewOnly"
```
> , където **SmartWebSite** е **CNAME** (Common name) на сертификата и
**SmartWebViewOnly** e сървис акаунта например;

* Отворете **Web.config** от главната инсталационна директория
(например  
"**C:\\Program Files\\Smartsys Ltd\\Smart OPC XML Server\\Web.config"**). Открийте следното:

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1\">
    <probing privatePath="Lib" />
</assemblyBinding>
```

и променте `privatePath="Lib"` на `privatePath="Lib;Bin"`.

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1\">
    <probing privatePath="Lib;Bin\" />
</assemblyBinding>
```

Това е необходимо за да се открият библиотеките при зареждане.

*``Внимание:`` Това е небходимо ако ASP .NET библиотеките не са
инсталирани.*