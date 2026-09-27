<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SaveToXml Method in Class SMS\_TaskSequence

The `SaveToXml` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager serializes a task sequence from WMI objects to XML.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
String SaveToXml(
      SMS_TaskSequence TaskSequence,
      SMS_TaskSequence_Reference References[],
      UInt32 Flags
);
```

#### Parameters

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: \[in\]

An [SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object representing the task sequence to serialize.

`References` Data type: `SMS_TaskSequence_Reference` Array

Qualifiers: \[out\]

[SMS\_TaskSequence\_Reference Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class) objects representing any packages and programs referenced in the XML that are required by the task sequence. The provider uses these objects to check against the packages and programs that exist on the site.

`Flags` Data type: `UInt32`

Qualifiers: \[out\]

Flags identifying serialization details. The only flag currently supported is 0x00000001, sequence deploys an operating system image.

## Return Values

A `String` data type containing the XML representation of the task sequence.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Important

Your application must use secure techniques when calling this method, because it retains all passwords \(secret information\) and product keys \(quasi-secret information\). It is secure if the XML is being saved to the database through the task sequence package. This method is not secure, however, if the XML is being saved to a file for use by another site. In this case, the call must be followed by a call to the [ExportXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence) to strip out the passwords and product keys.

Your application uses this method when saving task sequences and translating between task sequence WMI code and task sequence XML, preserving passwords and product keys. The most common use is by an outside provider that is manipulating the WMI object model.

Remember that this method does not serialize task sequence XML for an [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) object. For a package, you must reflect the task sequence XML using the <sequence></sequence> tags.

## Requirements

## See Also

[SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) [SMS\_TaskSequence\_Reference Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_reference-server-wmi-class) [ExportXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence)
