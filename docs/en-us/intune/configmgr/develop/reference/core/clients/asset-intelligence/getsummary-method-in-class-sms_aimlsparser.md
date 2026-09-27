<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aimlsparser -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSummary Method in Class SMS\_AIMLSParser

The `GetSummary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, retrieves the counts of imported Microsoft License count and non-Microsoft license count.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 MVLSCount;
     UInt32 NonMSLicenseCount;
);
```

#### Parameters

`MVLSCount` Data type: `UInt32`

Qualifiers: \[out\]

Returns the Microsoft License count.

`NonMSLicenseCount` Data type: `UInt32`

Qualifiers: \[out\]

Returns the non-Microsoft License count.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AIMLSParser Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aimlsparser-server-wmi-class)
