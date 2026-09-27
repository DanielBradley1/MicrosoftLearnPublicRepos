<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/cancelretire-method-in-class-sms_devicemethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CancelRetire Method in Class SMS\_DeviceMethods

The `CancelRetire` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, cancels the retirement of this device from Configuration Manager \(the device will remain managed by Configuration Manager\).

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CancelRetire(
   UInt32 ResourceId
);
```

#### Parameters

`ResourceId` Data type: `UInt32`

Qualifiers: \[in\]

ID of the resource.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## See Also

[SMS\_DeviceMethods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicemethods-server-wmi-class)
