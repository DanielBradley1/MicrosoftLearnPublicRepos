<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_eulacontent-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# SMS\_EULAContent Server WMI Class

The `SMS_EULAContent` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides information about optional configuration item content associated with Microsoft Software License Terms.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_EULAContent : SMS_BaseClass  
{  
    UInt32 EULAContentID;  
    String EULAContentUniqueID;  
    String EULAText;  
    String SourceSite;  
};  
```

## Methods

The `SMS_EULAContent` class does not define any methods.

## Properties

`EULAContentID`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

The unique ID of license terms content. This ID is unique only for the site.

`EULAContentUniqueID`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[unique\]

The unique ID of the license terms content. This ID is unique across sites.

`EULAText`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

Content of the license terms.

`SourceSite`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read, SizeLimit\("3"\)\]

The site code of the site where the license terms originate. The code string can have a maximum of three characters. For more information, see the `UpdateSource_ID` property in [SMS\_CIUpdateSources Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_ciupdatesources-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is applicable to all types of configuration items, not just software updates. For a discussion of configuration item types, see the `CIType_ID` property of [SMS\_ConfigurationItemBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitembaseclass-server-wmi-class).

  Your application should use this class only if the `EulaExists` property is set to `true` in the specified configuration item. This property is defined in the [SMS\_ConfigurationItemBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitembaseclass-server-wmi-class).

  To use this class, the application creates an `SMS_EULAContent` object and sets the properties as required for the software update.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments)
