<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/gettallyintervals-method-in-class-sms_summarizerrootstatus -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetTallyIntervals Method in Class SMS\_SummarizerRootStatus

The `GetTallyIntervals` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets an array of tally intervals and the default interval.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetTallyIntervals(
   String SiteCode,
    String ComponentName,
    String TallyIntervals[],
    String DefaultInterval
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: \[in, SizeLimit\("3"\)\]

The site code of the site for which the status is reported.

`ComponentName` Data type: `String`

Qualifiers: \[in, SizeLimit\("3"\)\]

The name of the component.

`TallyIntervals` Data type: `String` Array

Qualifiers: \[out\]

The tally intervals.

`DefaultInterval` Data type: `String`

Qualifiers: \[out\]

The default interval.

## Return Values

An `SInt32` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SummarizerRootStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class)
