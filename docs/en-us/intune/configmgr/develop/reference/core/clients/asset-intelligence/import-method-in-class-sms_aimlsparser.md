<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/import-method-in-class-sms_aimlsparser -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Import Method in Class SMS\_AIMLSParser

The `Import` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports the MLS statement as specified by the `MLSFilepath` parameter \(in UNC format\) into the Configuration Manager database.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 Import(
     String MLSFilepath,
     UInt32 Flags
);
```

#### Parameters

`MLSFilepath` Data type: `String`

Qualifiers: \[in\]

The UNC path of the .csv file to be imported.

`Flags` Data type: `UInt32`

Qualifiers: \[in\]

Specifies the type of data the .csv file contains, specified by the `MLSFilepath` property.

| Value | Description |
| --- | --- |
| 0 | Microsoft licenses. |
| Non 0 | Any non-Microsoft licenses. |

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
