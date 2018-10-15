You can connect to the **Experion PKS OPC** either by running the **Smart OPC XML Server** service under credentials that have granted access to the **EPKS OPC DA/HDA** or to initialize **COM** security and to provide windows **Username** and **Password** for each **OPC DA/HDA** connection.

- Create **Windows** group, in the operating system where **Honeywell EPKS** is placed, with name "**Local View Only Smart Web**" and description "**Smart Web View Only Local Group**";

- Create **Windows** user with name "**SmartWebViewOnly**" and description "**Smart Web View Only**" and set password;

- Assign "**SmartWebViewOnly**" user to be member of the "**Local View Only Smart Web**" group;

- Optionally you can make the group to be a member of the "**ViewOnly**" **Experion PKS** group, thus the user will be able to read only data from **Experion ODBC Driver** if you plan to install **Smart OData Services**;

- On the **Experion PKS** operating system start the **Component Services (**in the **Run** box or terminal window type "**dcomcnfg**" and hit **Enter**. Expand **Console Root** **\>Component Services \> Computers \> DCOM Config** and find nodes with name **Experion PKS OPC Server** (no suffix or 2,3,4,5). On every node you plan to connect with the **Smart OPC XML Server** right click and choose **Properties**. In the **Security** tab on "**Launch and Activation Permissions**" and "**Access Permissions**" add the "**Local View Only Smart Web**" group with permissions set to **Allow** for the **Local** and **Remote Launch** and **Activation** permissions. Press **OK** when done.

Now when configuring **OPC DA / HDA** plugin connections set **InitializeCOMSecurity** to true:

```xml
<IntitalizeCOMSecurity>true</IntitalizeCOMSecurity>
```

In **OpcConnection** add **Username**="**SmartWebViewOnly**" and
**Password**="**type SmartWebViewOnly password here"**:

```xml
<OpcConnection Url="opcda://epks-server-name-or-ip/HWHsc.OPCServer2" ... 
Username="SmartWebViewOnly" Password="type SmartWebViewOnly password here"/>
```

To grant read only **OPC DA/HDA** access to the "**Local View Only Smart Web**" group, open **Windows Explorer** and navigate to "**C:\\ProgramData\\Honeywell\\ProductConfig\\Security**" folder. On every file starting with "**XPKSOPCWrite**" or "**XPKSOPCHDAWrite**" right click and open **Properties**. On the **Security** tab, for group "**Local View Only Smart Web**" **deny** all permissions.

For more information about **EPKS OPC** security refer to the **Honeywell EPKS** product documentation.