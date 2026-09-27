<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/removetype-method-in-class-sms_usermachinerelationship -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RemoveType Method in Class SMS\_UserMachineRelationship

The `RemoveType` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, removes a type of the relationship between a user and a device.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 RemoveType(
     uint32 TypeId
);
```

#### Parameters

`TypeId` Data type: `UInt32`

Qualifiers: `[in]`

The type ID.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
