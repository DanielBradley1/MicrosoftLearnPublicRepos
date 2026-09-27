<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSequence Method in Class SMS\_TaskSequencePackage

The `GetSequence` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets a task sequence \([SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) from a task sequence package \([SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)\).

The following syntax is simplified from Managed Object Format \(MOF\) code, and it defines the method.

## Syntax

```
SInt32 GetSequence(
      SMS_TaskSequencePackage TaskSequencePackage,
      SMS_TaskSequence TaskSequence
);
```

#### Parameters

`TaskSequencePackage` Data type: `SMS_TaskSequencePackage`

Qualifiers: \[in\]

The task sequence package that contains the requested task sequence. See [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class).

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: \[out\]

The [SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object that represents the task sequence contained in the task sequence package specified in `TaskSequencePackage`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

Note

The task sequence is returned in the `TaskSequence` parameter.

## Remarks

You use `GetSequence` to get a [SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) WMI object that represents a task sequence from a task sequence package. With this object, you can make changes to the task sequence and then update the task sequence package by using the [SetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) [SetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage)
