<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SMS\_StateMigrationUserNames Server WMI Class

The `SMS_StateMigrationUserNames` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that represents a localized user name during state migration.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_StateMigrationUserNames
{
      UInt32 LocaleID;
      String UserName;
};
```

## Methods

The `SMS_StateMigrationUserNames` class doesn't define any methods.

## Properties

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the locale associated with the user name.

`UserName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The localized user name. The default value is "".

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application uses this class to create objects that are embedded by the [SMS\_StateMigration Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class) and accessed using the `UserNames` property. For an example of the use of this class, see How to Create an Association Between Two Computers in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_StateMigration server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class)
