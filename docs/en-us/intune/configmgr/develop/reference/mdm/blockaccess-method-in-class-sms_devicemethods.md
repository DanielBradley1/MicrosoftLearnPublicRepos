<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/blockaccess-method-in-class-sms_devicemethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# BlockAccess Method in Class SMS\_DeviceMethods

The `BlockAccess` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, blocks the Exchange ActiveSync device from accessing Exchange.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 BlockAccess(
   UInt32 ResourceId
   String EASIdentities[]
);
```

#### Parameters

`ResourceId` Data type: `UInt32`

Qualifiers: \[in\]

ID of the resource.

`EASIdentities` Data type: `String` Array

Qualifiers: \[in\]

Array of Exchange ActiveSync identities.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## See Also

[SMS\_DeviceMethods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class)
