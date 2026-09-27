<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemsettingreference-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ConfigurationItemSettingReference Server WMI Class

The `SMS_ConfigurationItemSettingReference` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides the rule relationship to the settings that are referenced from different configuration items.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationItemSettingReference : SMS_BaseClass
{
    UInt32 CI_ID;
    Boolean IsBroken;
    UInt32 Rule_ID;
    UInt32 Setting_ID;
    String SettingName;
};
```

## Methods

The `SMS_ConfigurationItemSettingReference` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`IsBroken` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

[SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class)

`Rule_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_ConfigurationItemRules Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemrules-server-wmi-class)

`Setting_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_ConfigurationItemSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemsettings-server-wmi-class).

`SettingName` Data type: `String`

Access type: Read/Write

Qualifiers: none

See [SMS\_ConfigurationItemSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemsettings-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
