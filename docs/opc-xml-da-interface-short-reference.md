# Overview

![](./media/image34.png)

## GetStatus

```csharp
ReplyBase GetStatus(string LocaleID, 
                    string ClientRequestHandle,
                    out ServerStatus Status)
```

![](./media/image35.png)
![](./media/image36.png)
![](./media/image37.png)

## Read

```csharp
ReplyBase Read(RequestOptions Options, 
               ReadRequestItemList ItemList, 
               out ReplyItemList RItemList, 
               out OPCError[] Errors)
```

![](./media/image38.png)
![](./media/image39.png)
![](./media/image40.png)
![](./media/image41.png)

![](./media/image42.png)
![](./media/image43.png)
![](./media/image44.png)
![](./media/image45.png)
![](./media/image46.png)

## Write
```csharp
ReplyBase Write(RequestOptions Options, 
                WriteRequestItemList ItemList, 
                bool ReturnValuesOnReply, 
                out ReplyItemList RItemList, 
                out OPCError[] Errors)
```
![](./media/image47.png)


## Subscribe

```csharp
ReplyBase Subscribe(RequestOptions Options, 
                    SubscribeRequestItemList ItemList, 
                    bool ReturnValuesOnReply, 
                    int SubscriptionPingRate, 
                    out SubscribeReplyItemList RItemList, 
                    out OPCError[] Errors, 
                    out string ServerSubHandle)
```

![](./media/image48.png)
![](./media/image49.png)
![](./media/image50.png)
![](./media/image51.png)

## SubscriptionPolledRefresh

```csharp
ReplyBase SubscriptionPolledRefresh(RequestOptions Options, 
                                    string[] ServerSubHandles, 
                                    DateTime HoldTime, 
                                    bool HoldTimeSpecified, 
                                    int WaitTime, 
                                    bool ReturnAllItems, 
                                    out string[] InvalidServerSubHandles, 
                                    out SubscribePolledRefreshReplyItemList[] RItemList, 
                                    out OPCError[] Errors, 
                                    out bool DataBufferOverflow)
```

![](./media/image52.png)

## SubscriptionCancel

```csharp
void SubscriptionCancel(string ServerSubHandle, 
                        ref string ClientRequestHandle)
```

## Browse

```csharp
ReplyBase Browse(XmlQualifiedName[] PropertyNames, 
                 string LocaleID, 
                 string ClientRequestHandle, 
                 string ItemPath, 
                 string ItemName, 
                 ref string ContinuationPoint, 
                 int MaxElementsReturned, 
                 browseFilter BrowseFilter, 
                 string ElementNameFilter, 
                 string VendorFilter, 
                 bool ReturnAllProperties, 
                 bool ReturnPropertyValues, 
                 bool ReturnErrorText, 
                 out BrowseElement[] Elements, 
                 out OPCError[] Errors, 
                 out bool MoreElements)
```

![](./media/image53.png)
![](./media/image54.png)
![](./media/image55.png)

## GetProperties

```csharp
ReplyBase GetProperties(ItemIdentifier[] ItemIDs, 
                        XmlQualifiedName[] PropertyNames, 
                        string LocaleID, 
                        string ClientRequestHandle, 
                        string ItemPath, 
                        bool eturnAllProperties, 
                        bool ReturnPropertyValues, 
                        bool ReturnErrorText, 
                        out PropertyReplyList[] ropertyLists, 
                        out OPCError[] Errors)
```

![](./media/image56.png)
![](./media/image57.png)