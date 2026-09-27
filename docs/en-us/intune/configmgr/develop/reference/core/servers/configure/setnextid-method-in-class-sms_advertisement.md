<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/setnextid-method-in-class-sms_advertisement -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetNextID Method in Class SMS\_Advertisement

The `SetNextID` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the ID number that will be used for the next advertisement created.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetNextID (
    UInt32 NextID
);
```

#### Parameters

`NextID` Data type: `UInt32`

Qualifiers: \[in\]

ID number for the next advertisement.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class)
