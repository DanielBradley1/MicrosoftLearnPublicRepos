<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/isclientoperationupdateallowed-method-in-class-sms_clientoperation -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IsClientOperationUpdateAllowed Method in Class SMS\_ClientOperation

The `IsClientOperationUpdateAllowed` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that checks whether a user has permission to update an operation.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 IsClientOperationUpdateAllowed
{
    [IN]    UInt32 OperationID
};
```

## Parameters

`OperationID` Data type: `UInt32`

Qualifiers: \[id\("0"\), in\]

OperationID.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
