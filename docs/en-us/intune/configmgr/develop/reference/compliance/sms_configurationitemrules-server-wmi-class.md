<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemrules-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ConfigurationItemRules Server WMI Class

The `SMS_ConfigurationItemRules` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents configuration item rules.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationItemRules : SMS_BaseClass
{
    UInt32 CI_ID;
    String CI_UniqueID;
    String ModelName;
    UInt32 Rule_ID;
    String Rule_UniqueID;
    String RuleDescription;
    String RuleName;
};
```

## Methods

The `SMS_ConfigurationItemRules` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`Rule_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

The database identifier of a rule defined in a configuration item.

`Rule_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Uniquely identifies a rule defined in the configuration item and is used for reporting rule level details.

`RuleDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the rule.

`RuleName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS\_CollectionRule Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
