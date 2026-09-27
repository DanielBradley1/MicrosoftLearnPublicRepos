<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/loadfromxml-method-in-class-sms_tasksequence -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# LoadFromXml Method in Class SMS\_TaskSequence

The `LoadFromXml` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, loads a task sequence into WMI objects from task sequence XML.

Caution

As of Configuration Manager SP1, `LoadFromXml` has been replaced by the `ImportSequence` method on the `SMS_TaskSequencePackage` server WMI class.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SMS_TaskSequence LoadFromXml(
      String Xml
);
```

#### Parameters

`Xml` Data type: `String`

Qualifiers: \[in\]

The task sequence XML to use to build the WMI objects.

## Return Values

An [SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Your application uses this method to import XML from an outside provider, for example, the user interface. It builds and returns a WMI object model based on the represented task sequence.

Caution

You should not make changes to task sequences by using the XML. Rather, you should use the task sequence object model to create and edit task sequences. For more information, see [Operating System Deployment Task Sequence Object Model](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequence-object-model).

Note

Use the [SetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage) method to add a task sequence to a task sequence package.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)
