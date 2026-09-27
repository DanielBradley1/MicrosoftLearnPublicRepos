<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getadvertisements-method-in-class-sms_advertisement -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetAdvertisements Method in Class SMS\_Advertisement

The `GetAdvertisements` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the advertisement id for a computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetAdvertisements(
     uint32  ResourceID,
     string  AdvertisementIDs[]
);
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: `[in]`

Unique Configuration Manager-supplied ID for the resource.

`AdvertisementIDs` Data type: `String` Array

Qualifiers: `[out]`

An array of unique auto-generated keys that Configuration Manager assigns to advertisements.

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
