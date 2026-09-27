<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/addsoftwarehashdata-method-in-class-sms_aisoftwarelist -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddSoftwareHashData Method in Class SMS\_AISoftwareList

The `AddSoftwareHashData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds the `SoftwarePropertiesHash` from `SoftwareCode` and `Title`.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddSoftwareHashData(
     UInt32 SoftwareTitles,
     UInt32 SoftwareHashs
);
```

#### Parameters

`SoftwareTitles` Data type: `UInt32`

Qualifiers: \[out\]

Count of software titles inserted during this method call.

`SoftwareHashs` Data type: `UIn32`

Qualifiers: \[out\]

Count of software hashes inserted during this method call.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AISoftwareList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class)
