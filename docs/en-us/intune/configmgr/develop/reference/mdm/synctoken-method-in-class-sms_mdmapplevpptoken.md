<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/synctoken-method-in-class-sms_mdmapplevpptoken -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SyncToken Method in Class SMS\_MDMAppleVppToken

The `SyncToken` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, initiates a synchronization of the Apple Volume Purchase Program \(VPP\) token.

## Syntax

```
sint32 SyncToken(
     String TokenID
);
```

#### Parameters

`TokenID` Data type: `String`

Qualifiers: \[in\]

The ID of the Apple VPP token.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MDMAppleVppToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmapplevpptoken-server-wmi-class)
