<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_os_details-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_OS\_Details Server WMI Class

The `SMS_OS_Details` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that describes the supported platforms \(operating system, architecture, and versions\) on which a program can run.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_OS_Details
{
      String MaxVersion;
      String MinVersion;
      String Name;
      String Platform;
};
```

## Methods

The `SMS_OS_Details` class doesn't define any methods.

## Properties

`MaxVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

The maximum operating system version of the range that is described by this class. The default value is "".

`MinVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

The minimum operating system version of the range described by this class. The default value is "".

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the operating system. The default value is "".

`Platform` Data type: `String`

Access type: Read/Write

Qualifiers: None

The hardware platform on which the operating system runs.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  The values you specify in this class must come from the [SMS\_SupportedPlatforms Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatforms-server-wmi-class) class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class) [How to Modify the Supported Platforms for a Program](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-modify-the-supported-platforms-for-a-program)
