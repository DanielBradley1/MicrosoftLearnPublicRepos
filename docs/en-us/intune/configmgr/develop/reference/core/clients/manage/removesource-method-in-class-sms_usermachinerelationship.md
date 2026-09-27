<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/removesource-method-in-class-sms_usermachinerelationship -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RemoveSource Method in Class SMS\_UserMachineRelationship

The `RemoveSource` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, removes a source for the relationship between a user and a device.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 RemoveSource(
     uint32 SourceId
);
```

#### Parameters

`SourceId` Data type: `UInt32` Array

Qualifiers: `[in]`

Source object identifier for dependency.

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
