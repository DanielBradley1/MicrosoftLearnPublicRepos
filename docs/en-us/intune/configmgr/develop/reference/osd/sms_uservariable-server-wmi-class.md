<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_uservariable-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SMS\_UserVariable Server WMI Class

The `SMS_UserVariable` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that defines the settings of a specific user \(such as IsCloudUser=True/False\).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_UserVariable
{
      Boolean IsMasked;
      String Name;
      String Value;
};
```

## Methods

The `SMS_UserVariable` class doesn't define any methods.

## Properties

`IsMasked` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

This property isn't currently used.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

The name of the user variable. The default value is "".

`Value` Data type: `String`

Access type: Read/Write

Qualifiers: None

The user variable value. The default value is `null`.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application uses this class to create objects that are embedded by the SMS\_UserSettings Server WMI Class and accessed by using the `UserVariables` property.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CollectionVariable Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_collectionvariable-server-wmi-class)
