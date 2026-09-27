<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/setdevicecategory-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetDeviceCategory Method in Class SMS\_Collection

The `SetDeviceCategory` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, assigns a category to a set of devices.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetDeviceCategory (
    String CategoryID,
    UInt32 ResourceIDs[]
);
```

#### Parameters

`CategoryID` Data type: `String`

Qualifiers: \[in\]

A device category ID. This value is a GUID in string format.

`ResourceIDs` Data type: `UInt32 Array`

Qualifiers: \[in\]

An array of resource IDs. The items in the array represent the devices to which the category is to be assigned.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
