<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/removemultipleresourceids-method-in-class-sms_mdmdeviceenrollmentmanagers -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RemoveMultipleResourceIds Method in Class SMS\_MDMDeviceEnrollmentManagers

The `RemoveMultipleResourceIds` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, deletes multiple resource IDs.

## Syntax

```
 sint32 RemoveMultipleResourceIds(
     UInt32 ResourceIds
);
```

#### Parameters

`ResourceIds` Data type: `UInt32 Array`

Qualifiers: \[in\]

Resource IDs.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MDMDeviceEnrollmentManagers Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmdeviceenrollmentmanagers-server-wmi-class)
