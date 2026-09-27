<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_category_localizedproperties-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Category\_LocalizedProperties Server WMI Class

The `SMS_Category_LocalizedProperties` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that describes various localized properties for a category, for example, a product or a classification.

## Syntax

```
Class SMS_Category_LocalizedProperties
{
      String CategoryInstanceName;
      UInt32 LocaleID;
};
```

## Methods

The `SMS_Category_LocalizedProperties` class doesn't define any methods.

## Properties

`CategoryInstanceName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Display name of the category instance. The default value is "".

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID for the locale associated with the category instance.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application uses this class to create objects that are embedded by [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class)
