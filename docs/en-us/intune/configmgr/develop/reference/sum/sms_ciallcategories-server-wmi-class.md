<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_ciallcategories-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIAllCategories Server WMI Class

The `SMS_CIAllCategories` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that lists all of the SMS\_CategoryInstance Server WMI Class or [SMS\_UpdateCategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatecategoryinstance-server-wmi-class) object instances for a given SMS\_ConfigurationItem object.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIAllCategories : SMS_BaseClass
{
    UInt32 CategoryInstanceID;
    String CategoryInstance_UniqueID;
    String CategoryTypeName;
    UInt32 CI_ID;
    String CI_UniqueID;
    String LocalizedCategoryInstanceName;
    UInt32 LocalizedPropertyLocaleID;
    String ModelName;
    UInt32 ObjectTypeID;
};
```

## Methods

The `SMS_CIAllCategories` class does not define any methods.

## Properties

`CategoryInstanceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read, Not\_null\]

Configuration Manager-generated, site-specific ID for the category instance. This ID is defined by the `CategoryInstanceID` property of SMS\_CategoryInstanceBase Server WMI Class for the specific configuration item.

`CategoryInstance_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[unique, SizeLimit\("512"\)\]

The unique ID for the category instance. This string can have a maximum of 512 characters. This ID is defined by the `CategoryInstance_UniqueID` property of SMS\_CategoryInstanceBase Server WMI Class for the specific configuration item.

`CategoryTypeName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read, Not\_null\]

The unique ID of the configuration item. This ID is unique only for the site. The ID is defined by the `CI_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class for the specific configuration item.

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is applicable to all types of configuration items, not just software updates. For a discussion of configuration item types, see the `CIType_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

  Use this class to query for all categories associated with a configuration item, or all configuration items associated with a category.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_UpdateCategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatecategoryinstance-server-wmi-class) [About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments)
