<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_Reference Server WMI Class

The `SMS_TaskSequence_Reference` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the package ID and optional program name used by the task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_Reference
{
      String Package;
      String Program;
      UInt32 Type
};
```

## Methods

The `SMS_TaskSequence_Reference` class does not define any methods.

## Properties

`Package` Data type: `String`

Access type: Read/Write

Qualifiers: None

If `Type` is 0, the identifier of the package. If `Type` is 1, the identifier of the application \(the model name\).

`Program` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional. The name of the program associated with the package. See [SMS\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class).

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The type of reference. The possible values are:

| Value | Reference type |
| --- | --- |
| 0 | Package Reference |
| 1 | Application Reference |

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

Your application can obtain the packages referenced by a task sequence from the `References` property of [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)
