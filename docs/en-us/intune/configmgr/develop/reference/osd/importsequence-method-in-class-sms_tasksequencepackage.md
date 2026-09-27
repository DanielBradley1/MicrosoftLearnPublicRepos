<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/importsequence-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ImportSequence Method in Class SMS\_TaskSequencePackage

The `ImportSequence` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports a task sequence package file based on the provided XML data of a previously exported task sequence package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ImportSequence(
      String SequenceXML,
      SMS_TaskSequence TaskSequence
);
```

#### Parameters

`SequenceXML` Data type: `String`

Qualifiers: \[in\]

A `string` variable which contains the XML data of the task sequence package to import.

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: \[out\]

The produced `SMS_TaskSequence` object.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)
