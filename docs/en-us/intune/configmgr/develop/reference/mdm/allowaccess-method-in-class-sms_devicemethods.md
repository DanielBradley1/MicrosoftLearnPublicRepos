<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/allowaccess-method-in-class-sms_devicemethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AllowAccess Method in Class SMS\_DeviceMethods

The `AllowAccess` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, lets the Exchange ActiveSync device connect to Exchange.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AllowAccess(
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
