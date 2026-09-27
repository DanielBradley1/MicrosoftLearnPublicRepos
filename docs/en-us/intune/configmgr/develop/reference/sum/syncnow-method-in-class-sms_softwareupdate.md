<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/syncnow-method-in-class-sms_softwareupdate -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# SyncNow Method in Class SMS\_SoftwareUpdate

The `SyncNow` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, performs a manual synchronization of the Software Update Point.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SyncNow(  
     Boolean fullSync  
);  
```

#### Parameters

`fullSync`  
Data type: `Boolean`

Qualifiers: \[in\]

`true` if a full sync should be performed. The default value is `false`.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class)
