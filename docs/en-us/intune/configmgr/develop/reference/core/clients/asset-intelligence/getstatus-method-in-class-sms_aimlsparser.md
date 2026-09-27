<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getstatus-method-in-class-sms_aimlsparser -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetStatus Method in Class SMS\_AIMLSParser

The `GetStatus` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, which is used to monitor the status of a previous call to the `Import` method.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetStatus(
     SInt32 Status
);
```

#### Parameters

`Status` Data type: `SInt32`

Qualifiers: \[out\]

When 0, indicates a successful call to `Import`.

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
