<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizationsettings-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SummarizationSettings Server WMI Class

The `SMS_SummarizationSettings` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the site summarization settings for a site.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizationSettings : SMS_BaseClass
{
    String ComponentName;
};
```

## Methods

The following table lists the methods in the `SMS_SummarizationSettings` class.

| Method | Description |
| --- | --- |
| [GetSummarizationSettings Method in Class SMS\_SummarizationSettings](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/getsummarizationsettings-method-in-class-sms_summarizationsettings) | Gets the summarization schedule. |
| [SetSummarizationSettings Method in Class SMS\_SummarizationSettings](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/setsummarizationsettings-method-in-class-sms_summarizationsettings) | Sets the summarization schedule. |

## Properties

`ComponentName` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null, read\]

Name of the Configuration Manager component.

## Remarks

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
