<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetSequence Method in Class SMS\_TaskSequencePackage

The `SetSequence` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates the task sequence package with the specified task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetSequence(
      SMS_TaskSequencePackage TaskSequencePackage,
      SMS_TaskSequence TaskSequence,
      String SavedTaskSequencePackagePath
);
```

#### Parameters

`TaskSequencePackage` Data type: `SMS_TaskSequencePackage`

Qualifiers: \[in\]

The package that the task sequence `TaskSequence` is added to. See [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class).

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: \[in\]

The [SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object that represents the task sequence that is added to `TaskSequencePackage`.

`SavedTaskSequencePackagePath` Data type: `String`

Qualifiers: \[out\]

The relative WMI object path for the updated task sequence package.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

`SetSequence` is used to associate a task sequence \([SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) with a task sequence package.

This method also updates other properties of the task sequence package, for example, package references and task sequence type, based on the specified task sequence.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) [GetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage)
