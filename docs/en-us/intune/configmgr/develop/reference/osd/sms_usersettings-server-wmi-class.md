<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_usersettings-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_UserSettings Server WMI Class

The `SMS_UserSettings` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that describes attributes that are specific to a single user that is managed by Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_UserSettings
{
      DateTime LastModificationTime;
      UInt32 LocaleID;
      SMS_UserVariable UserVariables[];
      UInt32 ResourceID;
};
```

## Methods

The `SMS_UserSettings` class does not define any methods.

## Properties

`LastModificationTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

The date and time when the user settings were last modified.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The ID of the locale used to convert the localized name and description of the user. The default locale ID is 1033, English \(United States\).

`UserVariables` Data type: `SMS_UserVariable` Array

Access type: Read/Write

Qualifiers: \[lazy\]

The SMS\_UserVariable Server WMI Class objects representing user variables for the user resource.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Key\]

The unique resource ID for the user.

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application can use this class as described in How to Create a Computer Variable in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_UserVariable Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_machinevariable-server-wmi-class)
