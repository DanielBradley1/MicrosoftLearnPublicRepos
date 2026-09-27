<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CategoryInstance Server WMI Class

The `SMS_CategoryInstance` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a category instance used to replicate information about a category, for example, a product or a classification, to all child sites. This class is used in settings management monitoring.

## Syntax

```
Class SMS_CategoryInstance : SMS_CategoryInstanceBase
{
      String CategoryInstance_UniqueID;
      UInt32 CategoryInstanceID;
      String CategoryTypeName;
      String LocalizedCategoryInstanceName;
      SMS_Category_LocalizedProperties LocalizedInformation[];
      UInt32 LocalizedPropertyLocaleID;
      UInt32 ParentCategoryInstanceID;
      String SourceSite;
};
```

## Methods

The `SMS_CategoryInstance` class does not define any methods.

## Properties

`CategoryInstance_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[unique, SizeLimit\("512"\)

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`CategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`CategoryTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`LocalizedCategoryInstanceName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`LocalizedInformation` Data type: `SMS_Category_LocalizedProperties` Array

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`ParentCategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  To use this class, the application creates an `SMS_CategoryInstance` object and sets the properties, as required, for the particular baseline configuration item.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class) [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class) [SMS\_ConfigurationBaselineInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class)
