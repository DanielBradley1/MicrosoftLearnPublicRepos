<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_alertemailtemplate-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AlertEmailTemplate Server WMI Class

The `SMS_AlertEmailTemplate` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the email template embedded by `SMS_Subscription`.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AlertEmailTemplate
{
    UInt32 AlertID,
    String Subject
};
```

## Methods

The `SMS_AlertEmailTemplate` class does not define any methods.

## Properties

`AlertID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier of the alert.

`Subject` Data type: `String`

Access type: Read/Write

Qualifiers: none

Subject of the email.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
