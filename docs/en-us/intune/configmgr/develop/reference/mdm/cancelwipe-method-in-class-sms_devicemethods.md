<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/cancelwipe-method-in-class-sms_devicemethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CancelWipe Method in Class SMS\_DeviceMethods

The `CancelWipe` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, cancels a pending wipe request on mobile devices or Exchange ActiveSync devices.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CancelWipe(
   UInt32 ResourceId
);
```

#### Parameters

`ResourceId` Data type: `UInt32`

Qualifiers: \[in\]

Identifier of the resource for which to cancel the wipe.

## Return Values

An `SInt32`data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## See Also

[SMS\_DeviceMethods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class)
