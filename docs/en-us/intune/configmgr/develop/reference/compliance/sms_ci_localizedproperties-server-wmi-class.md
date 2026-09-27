<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ci_localizedproperties-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CI\_LocalizedProperties Server WMI Class

The `SMS_CI_LocalizedProperties` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that contains the localized properties for a configuration item.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CI_LocalizedProperties
{
      String Description;
      String DisplayName;
      String InformativeURL;
      UInt32 LocaleID;
};
```

## Methods

The `SMS_CI_LocalizedProperties` class doesn't define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

Description of the configuration item. The default value is "".

`DisplayName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Display name for the configuration item. The default value is "".

`InformativeURL` Data type: `String`

Access type: Read/Write

Qualifiers: None

URL identifying additional information about the configuration item. The default value is "".

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the locale associated with the localized properties for the configuration item.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is embedded by the following classes, through the `LocalizedInformation` property:
- [SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class)
- [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)
- [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class)
- [SMS\_AuthorizationList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_authorizationlist-server-wmi-class)

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class) [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) [SMS\_AuthorizationList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_authorizationlist-server-wmi-class)
