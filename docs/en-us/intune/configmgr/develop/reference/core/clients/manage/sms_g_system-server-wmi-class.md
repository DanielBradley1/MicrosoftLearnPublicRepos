<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System Server WMI Class

The `SMS_G_System` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that serves as the abstract base class for all hardware and software system classes, for example, [SMS\_G\_System\_CI\_ComplianceState Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_g_system_ci_compliancestate-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System : SMS_Group
{
     UInt32 ResourceID;
};
```

## Methods

The `SMS_G_System` class does not define any methods.

## Properties

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_Group Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Group Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class)
