<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ci_localizedeulas-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CI\_LocalizedEulas Server WMI Class

The `SMS_CI_LocalizedEulas` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that contains the localized Microsoft Software License Terms information for a configuration item.

## Syntax

```
Class SMS_CI_LocalizedEulas
{
      String EULAContentUniqueID;
      UInt32 LocaleID;
};
```

## Methods

The `SMS_CI_LocalizedEulas` class does not define any methods.

## Properties

`EULAContentUniqueID` Data type: `String`

Access type: `Read/Write`

Qualifiers: `None`

Unique ID of the Microsoft Software License Terms content.

`LocaleID` Data type: `UInt32`

Access type: `Read/Write`

Qualifiers: `None`

The ID of the locale associated with the localized information.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is embedded by the following classes, through the `LocalizedEulas` property:
- [SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class)
- [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)
- [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class)

  Your application uses this class only if the `EULAExists` property of the configuration item is set to `true`.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class)
