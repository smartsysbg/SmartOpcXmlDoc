---
title: Свързване с Honeywell Experion PKS OPC DA/HDA
---

Може да се свържете с **Experion PKS OPC** или като стартирате 
**Smart OPC XML Server** услугата с потребител, който има достъп до 
**EPKS OPC DA/HDA** или да поставите на **InitializeCOMSecurity** стойност
"**true**" и да въведете windows **Username** и **Password** за всяка
**OPC DA/HDA** връзка.

Ако потребителя няма достъп до **EPKS OPC DA/HDA** направете следното на
**Experion PKS** сървъра:

- Създайте **Windows** група с име "**Local View Only Smart Web**";

- Създайте **Windows** потребител с име "**SmartWebViewOnly**";

- Назначете на потребител "**SmartWebViewOnly**" група "**Local View Only Smart Web**";

- Опционално може да настроите групата да е член на "**ViewOnly**"
**Experion PKS** група, по този начин потребителя ще може да чете от
**Experion ODBC Driver**, ако планирате да инсталирате **Smart OData
Services;**

- Стартирайте **Component Services (**в **Run** кутийката или терминал
напишете "**dcomcnfg**" и натиснете **Enter**). Открийте  **Console Root \> Component Services \> Computers \> DCOM Config** и
намерете възли с име **Experion PKS OPC Server** (без суфикс или с
2,3,4 или 5). На всеки възел, към който смятате да се свързвате
десен клик и изберете **Properties**. В **Security** таб-а на
"**Launch and Activation Permissions**" и на "**Access
Permissions**" добавете "**Local View Only Smart Web**" групата с
пермисии **Allow** за **Local** and **Remote Launch** and
**Activation**. Натиснете **OK**, когато сте готови. (Ако **EPKS**
сървърите са резервирани, тази операция трябва да се направи и на
двата сървъра)

Сега когато конфигурирате **OPC DA / HDA** връзки поставете
**InitializeCOMSecurity** на „**true**":

```xml
<IntitalizeCOMSecurity>true</IntitalizeCOMSecurity>
```

В **OpcConnection** добавете **Username**="**SmartWebViewOnly**" and
**Password**="**type SmartWebViewOnly password here"**:

```xml
<OpcConnection Url="opcda://epks-server-name-or-ip/HWHsc.OPCServer" ... 
Username="SmartWebViewOnly" Password="type SmartWebViewOnly password here"/>
```
Ако искате да ограничите **OPC DA/HDA** достъпа само за четене на
"**Local View Only Smart Web**" групата, отворете **Windows Explorer** и
навигирайте до  
"**C:\\ProgramData\\Honeywell\\ProductConfig\\Security**". На всеки файл
започващ с "**XPKSOPCWrite**" или "**XPKSOPCHDAWrite**" десен бутон с
мишката и изберете **Properties**. На **Security** таб-а, за група
"**Local View Only Smart Web**" изберете "**deny**" за всички разрешения.

За повече информация относно **EPKS OPC** сигурност се обърнете към
**Honeywell EPKS** продуктовата документация.

Ако използвате **InitializeCOMSecurity** и имате проблем със
**Subscribe** заявките, но другте операции работят, като **Browse, Read,
GetProperties**, може да се наложи да създадете същият потребителски
акаунт на **Smart OPC XML** сървъра, какъвто сте упоменали в
**OpcConnection** секцията със същата парола и единствено да му зададете
да бъде член на **Distributed COM Users** групата на операционната
система.