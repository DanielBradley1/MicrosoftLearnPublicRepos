<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/reporting/getsamplevalues-method-in-class-sms_reportviewschema -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSampleValues Method in Class SMS\_ReportViewSchema

The `GetSampleValues` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets sample values for a report view schema.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 GetSampleValues(
   UInt32 RangeBegin,
   UInt32 RangeEnd,
   String Filter,
   UInt32 TotalValuesAvailable,
   String Values[]
);
```

#### Parameters

`RangeBegin` Data type: `UInt32`

Qualifiers: \[in\]

Value indicating the beginning of the range of sample values.

`RangeEnd` Data type: `UInt32`

Qualifiers: \[in\]

Value indicating the end of the range of sample values.

`Filter` Data type: `String`

Qualifiers: \[in\]

Filter to use for retrieval of sample values.

`TotalValuesAvailable` Data type: `UInt32`

Qualifiers: \[out\]

The number of sample values retrieved in the `Values` parameter.

`Values` Data type: `String` Array

Qualifiers: \[out\]

The retrieved sample values.

## Return Values

A `UInt32` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ReportViewSchema Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/reporting/sms_reportviewschema-server-wmi-class)
