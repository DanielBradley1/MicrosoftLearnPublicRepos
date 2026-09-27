<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/getonlinecount-method-in-class-sms_cn_clientstatus -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetOnlineCount Method in Class SMS\_CN\_ClientStatus

The `GetOnlineCount` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that gets an online count of the selected clients of the target collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetOnlineCount
{
    [IN]    String TargetCollectionID
    [IN]    Uint32 TargetResourceIDs[]
};
```

## Parameters

`TargetCollectionID` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Target collection identifier.

`TargetResourceIDs` Data type: `UInt32` Array

Qualifiers: \[id\("1"\), in\]

Target client resource identifiers.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
