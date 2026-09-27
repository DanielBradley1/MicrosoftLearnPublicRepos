<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getpendingcomponentlist-method-in-class-ccm_application -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetPendingComponentList Method in Class CCM\_Application

The `GetPendingComponentList` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that gets the pending component list for an application.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetPendingComponentList
{
    [IN]    String AppDeliveryTypeId
    [IN]    UInt32 Revision
    [OUT]   String PendingComponentList
};
```

## Parameters

`AppDeliveryTypeId` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Application delivery type identifier.

`Revision` Data type: `UInt32`

Qualifiers: \[id\("1"\), in\]

Revision.

`PendingComponentList` Data type: `String`

Qualifiers: \[id\("2"\), out\]

Pending component list.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
