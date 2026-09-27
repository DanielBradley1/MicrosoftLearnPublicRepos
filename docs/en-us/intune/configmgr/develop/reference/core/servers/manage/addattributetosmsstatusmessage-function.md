<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/addattributetosmsstatusmessage-function -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddAttributeToSMSStatusMessage Function

In Configuration Manager, the `AddAttributeToSMSStatusMessage` function adds a single optional status message attribute ID/value pair to a status message object.

## Syntax

```
[C/C++]
typedef DWORD (WINAPI *PROC_ADDATTRIBUTETOSMSSTATUSMESSAGE)
(
      HANDLE hStatusMessageObject,
      DWORD  dwAttributeID,
      LPCSTR pszAttributeValue
);
```

#### Parameters

`hStatusMessageObject` Data type: `HANDLE`

Qualifiers: \[in\]

Handle to the status message object.

`dwAttributeID` Data type: `DWORD`

Qualifiers: \[in\]

Status message attribute ID.

`pszAttributeValue` Data type: `LPCSTR`

Qualifiers: \[in\]

Status message attribute value.

## Return Values

One of the values in the following table.

| Value | Description |
| --- | --- |
| SMSSTATMSG\_SUCCESS | The attribute ID/value pair was successfully added to the object. |
| SMSSTATMSG\_OUT\_OF\_MEMORY | This function failed to allocate enough memory to add the attribute ID/value pair to the object. |
| STATMSG\_ERROR\_INVALID\_ATTR\_VALUE | The caller supplied `null` or a string that exceeded SMSSTATMSG\_MAX\_ATTR\_VALUE\_LENGTH characters in length for the `pszAttributeValue`parameter. |
| SMSSTATMSG\_ERROR\_MAX\_ATTR\_LIMIT | The object already has SMSSTATMSG\_MAX\_NUM\_ATTRS attribute ID/value pairs associated with it, which is the maximum permitted number. |
| SMSSTATMSG\_ERROR\_UNKNOWN | Encountered an unknown error while trying to add the attribute ID/value pair. |

## Remarks

Smscstat.h includes the following #define for calling `AddAttributeToSMSStatusMessage` by using the Win32 function `GetProcAddress`.

```
#define PROCNAME_ADDATTRIBUTETOSMSSTATUSMESSAGE "AddAttributeToSMSStatusMessage"
```

All Configuration Manager status messages include a set of mandatory properties, such as the name of the component that reported the message, the message ID, the time the message was reported, and the insertion strings for the message. These mandatory properties are initialized when the status message object is created and by the parameters passed into the status message reporting API functions. In addition to the mandatory properties, a status message has zero or more optional properties associated with it. In the Configuration Manager status system, these optional properties are called attribute ID/value pairs or simply attributes. In Status Message Viewer, these optional properties appear in the **Properties** box when you double-click a status message to open the **Status Message Details** box.

Attribute ID/value pairs are associated with status messages to facilitate the construction of efficient status message queries. For example, when any Configuration Manager component reports a status message related to a particular Configuration Manager package \(a software distribution object\), the status message includes the package ID as an attribute ID/value pair. The administrator can execute a query to retrieve all the status messages associated with the package. The status message tables in the Configuration Manager SQL Server database are indexed to allow messages to be retrieved efficiently by attribute ID/value pairs.

An attribute ID/value pair is composed of a `DWORD` type as the attribute ID and a null-terminated ASCII string as the attribute data. The possible attribute IDs are listed in the following table. These IDs currently specify all object identifiers for objects that are specific to Configuration Manager that are associated with the Configuration Manager software distribution features. Unless your application is integrating with the software distribution functionality, it is highly unlikely that you need to associate any attribute ID/value pairs with any of the status messages to report. Therefore, it is highly unlikely that you ever need to call this function from an application.

| Value | Description |
| --- | --- |
| SMSSTATMSG\_ATTR\_ID\_PACKAGE\_ID \(400\) | The attribute value is the eight-character ID of a Configuration Manager package. |
| SMSSTATMSG\_ATTR\_ID\_ADVERTISEMENT\_ID \(401\) | The attribute value is the eight-character ID of a Configuration Manager advertisement. |
| SMSSTATMSG\_ATTR\_ID\_COLLECTION\_ID \(402\) | The attribute value is the eight-character ID of a Configuration Manager collection. |
| SMSSTATMSG\_ATTR\_ID\_USER\_NAME \(403\) | The attribute value is a Windows NT user name and domain of the form domain\\user name. In situations where the domain is not available, the attribute value takes the form of user name alone. |
| SMSSTATMSG\_ATTR\_ID\_DISTRIBUTION\_POINT \(404\) | The attribute value is a Configuration Manager NAL path for a Configuration Manager distribution point. |

## Requirements

Smscstat.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMSCSTAT.DLL Status Message Functions](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smscstat.dll-status-message-functions) [CreateSMSStatusMessage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/createsmsstatusmessage-function)
