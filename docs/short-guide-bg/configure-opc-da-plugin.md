---
title: Конфигуриране на OPC DA плъгин
---

**Smart OPC DA** плъгин се зарежда от **Smart OPC XML DA** модула.
Предназначението на този плъгин е да осигури връзка с класически **OPC DA** сървъри.

## Структура на директориите {: #directory-structure}

**&lt;InstallDir&gt;** - Инсталационна директория на приложението;

> **Plugins** - Директория на плъгините;
>> **OpcDa** - OPC DA плъгин;
>>> **Bin** - библиотеки специфични за плъгина;
>>>> **AddIns** - ад-ини на плъгина;
>>>>> **Slot0** - слот 0;  
>>>>> **Slot1** - слот 1;  
>>>>> **... **  
>>>>> **Slot14** - слот 14;

>>>> **AddInSideAdapters** - ад-ин адаптери;  
>>>> **AddInViews** - ад-ин вю-та;  
>>>> **Contracts** - контракти;  
>>>> **HostSideAdapters** - хост адаптери;

>>> **Config** - Конфигурация на плъгина;  
>>> **Logs** - лог файли;

## Конфигуриране на OPC DA връзка {: #configure-opc-da-connection}

Конфигурацията на **Smart** **OPC DA** плъгина се намира във файл  
**&lt;InstallDir&gt;\\Plugins\\OpcDa\\Config\\Smart.OpcXml.Plugin.Configuration.xml**.  
Плъгина поддържа връзки до различни **OPC DA** сървъри. Всяка връзка се
конфигурира чрез отделна "**OpcServer**" секция.

__Пример:__

```xml
<!-- EPKS-ESVR-1 -->
  <OpcServer Enabled="true" CheckConnectionStateInterval="3000" RequestExecutionTimeout="60000" MaxLongRunningRequests="1">
    <LoggerName>Smart.OpcXml.Plugins.OpcDa.AddIn.EPKS-ESVR-1</LoggerName>
    <SupportBrowse>true</SupportBrowse>
    <SupportGetProperties>true</SupportGetProperties>
    <SupportRead>true</SupportRead>
    <SupportWrite>true</SupportWrite>
    <SupportSubscribe>true</SupportSubscribe>
    <SupportGetStatus>true</SupportGetStatus>
    <SupportsContinuationPoint>true</SupportsContinuationPoint>
    <Alias>EPKS-ESVR-1</Alias>
    <PathSeparator>.</PathSeparator>
    <MinSubscriptionSamplingRate>1000</MinSubscriptionSamplingRate>
    <DefaultSubscriptionSamplingRate>3000</DefaultSubscriptionSamplingRate>
    <MaxSubscriptionItemBufferSize>10</MaxSubscriptionItemBufferSize>
    <DefaultSubscriptionPingRate>60000</DefaultSubscriptionPingRate>
    <MaxSubscribedItems>0</MaxSubscribedItems>
    <MaxSubscriptions>1000</MaxSubscriptions>
    <MaxItemsPerSubscription>4000</MaxItemsPerSubscription>
    <!-- Maximum allowed number of items per read list. 0 if no restrictions -->
    <MaxItemsPerRead>0</MaxItemsPerRead>
    <!-- Maximum allowed number of items per write list. 0 if no restrictions -->
    <MaxItemsPerWrite>0</MaxItemsPerWrite>
    <!-- Maximum allowed number of items per get properties list. 0 if no restrictions -->
    <MaxItemsPerGetProperties>0</MaxItemsPerGetProperties>
    <!-- The maximum items returned per browse request. 
	     If value is greater than 0, and MaxElementsReturned is 0 or greater than MaxItemsPerBrowse it will be forced to this value. 
	     If 0 there is no constraint. 
		 SupportsContiunationPoint must be set to "true" in order the restriction to be taken into account for this gateway. 
	 -->
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

    <!-- <DebugTraceFirstChanceExceptions>true</DebugTraceFirstChanceExceptions> -->
    <!-- <DebugTraceUnhandledExceptions>true</DebugTraceUnhandledExceptions> -->
    <!-- <DebugTraceIgnoreInvalidCastFirstChanceExceptions>true</DebugTraceIgnoreInvalidCastFirstChanceExceptions> -->
    <IntitalizeCOMSecurity>true</IntitalizeCOMSecurity>
    <OpcConnection Url="opcda://EPKS-ESVR-1A/HWHsc.OPCServer" Enabled="true" Priority="2000" UseDuplicates="true" Username="mngr" Password="****"/>
    <OpcConnection Url="opcda://EPKS-ESVR-1B/HWHsc.OPCServer" Enabled="true" Priority="1000" UseDuplicates="true" Username="mngr" Password="****"/>
    <!-- <SyncTokens Read="1" Write="1" Browse="1" Subscribe="1" SubscriptionCancel="1" GetProperties="1" GetStatus="1"></SyncTokens> -->
    <!-- 
		<SourceCodePage>1252</SourceCodePage> 
		<DestinationCodePage>1251</DestinationCodePage> 
	-->
  </OpcServer>
```

``Внимание:``

- Уверете, че сте разрешили "**Write**" операции (`<SupportWrite>true</SupportWrite>`), ако смятате да пишете;

- Псевдонима (`<Alias>EPKS-ESVR-1</Alias>`) трябва да е уникален, той влиза като част от пътя на параметъра в последствие, така че въвеждайте смислени имена за псевдоним. Ако има дублирания, дублираните връзки няма да се заредят;

- Задайте адекватно име на логъра  
(`<LoggerName>Smart.OpcXml.Plugins.OpcDa.AddIn.EPKS-ESVR-1</LoggerName>`),  името на псевдонима да участва в него, по този начин ще се ориентиране в логовете, кой за коя връзка отговаря.

\[**IntitalizeCOMSecurity**\]

Ако е "**true**" се извиква **CoInitializeSecurity**, което спира **Schannel** **COM** автентикацията.

*``Внимание:`` Използвайте тази опция, ако **Smart OPC XML Server**
процеса работи под акаунт , който няма достъп до класическия **OPC DA**
сървър. В случай, че е опцията е включена, трябва да посочите потребител
и парола за връзка класически **OPC DA** server, като потребителя на
**Smart** **OPC XML Server** процеса няма да се използва за
имеперсонализация на **DCOM** заявките.*

\[**Enabled**\]

Ако е "**true**" връзка е разрешена, в противен случай спряна;

\[**OpcConnection**\]

Описание на крайна точка за свързване с класически **OPC DA** съръвър. 
Може да въведете няколко връзки и да ги приоритизирате с "**Priority**" 
атрибута. По-голяма стойност означава по-голям приоритет. Специфицирането 
на повече от една връзка се използва за резервираност (примерно ако имате 2 
**EPKS** сървъра A и B).

**Url** - адрес на **OPC DA** сървъра (`opcda://computer name or ip address/DCOM service name or GUID`).

**Enabled** - Ако е "**true**", връзката е разрешена;

**Priority** - Приоритет на връзката. По-голяма стойност - по-голям
приоритет;

**Username** - Потребител за имперсонализация (само ако **InitializeCOMSecurity** е включено; за временна бърза връзка до
**EPKS** ползвайте **mngr** акаунта);

**Password** - Парола за имперсонализация (само ако 
**InitializeCOMSecurity** е включено; за временна бърза връзка до
**EPKS** ползвайте **mngr** акаунта);

**Domain** - Домейн за имперсонализация (само ако
**InitializeCOMSecurity** е включено; за временна бърза връзка до
**EPKS** ползвайте **mngr** акаунта);

**ProxyUri** - адрес на прокси за връзката, ако има такова;

**AlwaysUseDA20** - Ако е "**true**" използва само **OPC DA 2.0**
независимо дали **DCOM** сървъра поддържа **OPC DA 3.0**;

**LicesneKey** - Лицензен ключ, ако **OPC DA** server го изисква;

**UseDiplicates** - Ако "**true**" и протокола е **OPC DA 2.0**, тогава
при браузване на адресното пространстово на сървъра ще се отваря нова
връзка, след което ще я затваря. По този начин е възможно конкурентно
бразуване, в противен случай заявките ще се изчакват;

**MaxDuplicates** - Максимнален борй на дублираните връзки за
браузване. След изчерпване потребителите се изчакват. 0 няма
ограничение.

## Слотове {: #slots}

Всяка конфигурирана и разрешена връзка до **OPC DA** сървър, описана в
**OpcServer** секция, използва един слот. По подразбиране има 15 слота
(**Slot0**-**14**). Ако сте конфигурирали повече разрешени връзки до
**OPC DA** сървъри от колкото слотовете имате, част от връзките няма да
работят. Може да увеличите броя на слотовете, като създадете нова
под-директория в **AddIns** и да я именувате следваща поредна, например
**Slot15**, и да копирате съдържанието на **Slot0** в нея.