<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_summarizationinterval-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SummarizationInterval Server WMI Class

The `SMS_SummarizationInterval` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the months that have been summarized by a monthly usage summary.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizationInterval : SMS_BaseClass
{
      DateTime IntervalStart;
      UInt32 TimeKey;
};
```

## Methods

The `SMS_SummarizationInterval` class does not define any methods.

## Properties

`IntervalStart` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the software metering interval starts.

`TimeKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Key that uniquely identifies the interval, equivalent to 100\*Year+Month.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

This class is the source for the `TimeKey` property in a monthly usage summary represented by [SMS\_MonthlyUsageSummary Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_monthlyusagesummary-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MonthlyUsageSummary Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_monthlyusagesummary-server-wmi-class)
