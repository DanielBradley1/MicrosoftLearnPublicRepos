<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_applicationcondition-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ApplicationCondition Server WMI Class

The `SMS_ApplicationCondition` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents relationships between global conditions and applications.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ApplicationCondition : SMS_BaseClass
{
    String ApplicationGUID;
    String ConditionDisplayName;
    UInt32 ConditionID;
    String ConditionModelName;
};
```

## Methods

The `SMS_ApplicationCondition` class does not define any methods.

## Properties

`ApplicationGUID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Unique identifier of the application.

`ConditionDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Condition display name.

`ConditionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Identifier of the application condition.

`ConditionModelName` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Model name of the condition.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
