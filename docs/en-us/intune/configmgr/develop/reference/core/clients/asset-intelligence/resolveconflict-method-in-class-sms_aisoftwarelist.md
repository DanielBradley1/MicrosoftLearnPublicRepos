<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/resolveconflict-method-in-class-sms_aisoftwarelist -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ResolveConflict Method in Class SMS\_AISoftwareList

The `ResolveConflict` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, is used to resolve conflicts that result by creating or editing software entries, and the same software entry being created by Microsoft through the online synchronization.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ResolveConflict(
     String SoftwareKey,
     UInt32 Resolution
);
```

#### Parameters

`SoftwareKey` Data type: `String`

Qualifiers: \[in\]

The MD5 hash of the software entry, which has a conflict to be resolved. The hash is made up of the software name, publisher, and version.

This property name has changed from `SoftwarePropertiesHash` to `SoftwareKey` in SP1.

`Resolution` Data type: `UInt32`

Qualifiers: \[in\]

Action to take on the software entry.

| Value | Description |
| --- | --- |
| 1 | Keep the local copy and discard any updates from Microsoft. |
| 2 | Revert the local copy and replace it with latest update from Microsoft. |

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
