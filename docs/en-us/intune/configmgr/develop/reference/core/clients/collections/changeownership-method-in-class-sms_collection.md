<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/changeownership-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ChangeOwnership Method in Class SMS\_Collection

The `ChangeOwnership` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, changes ownership of the devices.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ChangeOwnership(
     UInt32 ResourceIDs[],
     UInt32 DeviceOwner
     SInt32 ReturnValue
);
```

#### Parameters

`ResourceIDs` Data type: `UInt32` Array

Qualifiers: \[in\]

IDs of member resources.

`DeviceOwner` Data type: `UInt32`

Qualifiers: \[in\]

The new owner of the machines.

| Value | Device owner |
| --- | --- |
| 1 | Company |
| 2 | Personal |

`ReturnValue` Data type: `SInt32`

Qualifiers: \[out\]

The number of devices that were successfully reassigned ownership.

Important

Even if there is an error, some devices may still get reassigned ownership.

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
