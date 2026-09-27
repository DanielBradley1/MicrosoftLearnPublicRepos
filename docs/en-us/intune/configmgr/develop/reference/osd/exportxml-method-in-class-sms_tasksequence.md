<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportxml-method-in-class-sms_tasksequence -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ExportXml Method in Class SMS\_TaskSequence

The `ExportXml` Windows Management Instrumentation\(WMI\) class method, in Configuration Manager, exports task sequence XML in a format that is suitable to use on another site.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
String ExportXml(
      String Xml
);
```

#### Parameters

`Xml` Data type: `String`

Qualifiers: \[in\]

The task sequence XML. This XML comes from a previous call to the [SaveToXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence).

## Return Values

A `String` data type defining the exported task sequence XML.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Important

Your application must use secure techniques when calling the [SaveToXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence) method, because it retains all passwords \(secret information\) and product keys \(quasi-secret information\). Used by itself, this method is not secure when used for saving XML to a file for use by another site.

Your application uses `ExportXml` to translate between task sequence WMI code and task sequence XML. It first calls the [SaveToXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence) to create task sequence XML, preserving passwords and product keys. Then the application must call `ExportXml` and save the resulting information to a file, clearing all passwords \(secret information\) and product keys \(quasi-secret information\).

Remember that this method does not serialize task sequence XML for an [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) object. For a package, you must reflect the task sequence XML by using the <sequence></sequence> tags.

## Requirements

## See Also

[SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) [SaveToXml Method in Class SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/savetoxml-method-in-class-sms_tasksequence)
