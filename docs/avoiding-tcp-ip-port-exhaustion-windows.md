In environments with a very high number of web requests per second, or with 
a high number of web services/references integrations, you might find that 
the application\'s performance is lower then what you would expect from 
that system, or even worse, the applications or web services stop 
responding completely or generate timeout errors, even though your 
system\'s resources (CPU, RAM or Network bandwidth) don\'t seem to be 
exhausted at all. Although the causes for such symptoms can vary, there\'s 
one scenario that can cause a complete lock of systems handling a very 
large number of web requests per second without any hint of what\'s going 
on: TCP/IP port exhaustion.

Reduce the **TIME\_WAIT** by setting the [TcpTimedWaitDelay](http://www.outsystems.com/forums/discussion/6956/How+to+tune+the+TCP%2FIP+stack+for+high+volume+of+web+requests/) **TCP/IP** parameter
to **30 seconds** on the windows registry
key **HKLM\\SYSTEM\\CurrentControlSet\\Services\\Tcpip\\Parameters**, as
a **DWORD** value.

You may have to set the **StrictTimeWaitSeqCheck** as well, for **TcpTimedWaitDelay** to be of effect:

```reg
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters]
"StrictTimeWaitSeqCheck"=dword:00000001
```
Increase the upper range of ephemeral ports that are dynamically allocated to client **TCP/IP** socket connections:

```reg
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters]
"MaxUserPort"=dword:<Enter a decimal value between 5000 and 65534 here>
```
or increase the range of ephemeral ports by setting the [**dynamicportrange **](http://technet.microsoft.com/en-us/library/cc731521%28WS.10%29.aspx#BKMK_setdynamicportrange) to an higher value through the command 
`netsh int ipv4 set dynamicportrange tcp start=32767 num=32768`, this will set the port range from **32768** to **65535**.

Setting or changing these will require a reboot for the changes to be in
effect. 

More info:


<https://msdn.microsoft.com/en-us/library/aa560610(v=bts.20).aspx>  
<http://www.outsystems.com/forums/discussion/6956/How+to+tune+the+TCP%2FIP+stack+for+high+volume+of+web+requests/>