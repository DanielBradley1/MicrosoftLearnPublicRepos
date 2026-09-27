<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence Server WMI Class

The `SMS_TaskSequence` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an operating system deployment task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence
{
      String SchemaVersion;
      SMS_TaskSequence_Step Steps[];
};
```

## Methods

The following table shows the methods in `SMS_TaskSequence`.

| Method | Description |
| --- | --- |
| [ExportXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence) | Exports task sequence XML in a format that is suitable to use on another site. |
| [LoadFromXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/loadfromxml-method-in-class-sms_tasksequence) | Loads a task sequence into WMI objects from XML. |
| [SaveToXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence) | Serializes a task sequence from WMI objects to XML. |

## Properties

`SchemaVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

The version of the task sequence schema. The default version number is 3.00.

Although this property is designated as read/write in WMI, your application should not change it. The schema version must match the version that is detected by the client, or the client does not run the task sequence.

`Steps` Data type: `SMS_TaskSequence_Step` Array

Access type: Read/Write

Qualifiers: None

[SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) objects representing steps and conditions in the task sequence.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Provider\("TaskSequenceProvider"\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  A task sequence is a series of steps and conditions that are processed during operating system deployment.

  A step in the task sequence is usually an action, represented by the [SMS\_TaskSequence\_Action Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) or a derived class. A task sequence step can also be a set of actions in a group, represented by [SMS\_TaskSequence\_Group Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class). For more information, see [SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class).

  Task sequence steps are managed using WMI. The sequence steps are processed in order and can have conditions associated with them that determine how the action, or group of actions, is processed. For more information, see Operating System Deployment Task Sequence Object Model.

  Your application uses `SMS_TaskSequence` objects through a [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) object, which supports a `Sequence` property to wrap the task sequence in the database. The application sets up a new task sequence by calling the [SetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage) and accesses an existing task sequence using the [GetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage). For more information about working with a task sequence, see How to Create an Operating System Deployment Task Sequence and How to Create an Operating System Deployment Task Sequence Package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence\_ConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionexpression-server-wmi-class) [SMS\_TaskSequence\_Group Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class) [SMS\_TaskSequence\_Step Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)
