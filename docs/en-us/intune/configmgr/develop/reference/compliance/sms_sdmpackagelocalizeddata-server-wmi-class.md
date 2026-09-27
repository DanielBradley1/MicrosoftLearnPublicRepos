<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_sdmpackagelocalizeddata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SDMPackageLocalizedData Server WMI Class

The `SMS_SDMPackageLocalizedData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents localized data for a System Definition Model \(SDM\) package.

## Syntax

```
Class SMS_SDMPackageLocalizedData
{
      UInt32 LocaleID;
      String LocalizedData;
};
```

## Methods

The `SMS_SDMPackageLocalizedData` class does not define any methods.

## Properties

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The ID of the locale associated with the localized information.

`LocalizedData` Data type: `String`

Access type: Read/Write

Qualifiers: None

The localized data.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is embedded by the [SMS\_ConfigurationItemBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitembaseclass-server-wmi-class) through the `SDMPackageLocalizedData` property.

  The application uses this class to add localized string resources to the server database.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class)
