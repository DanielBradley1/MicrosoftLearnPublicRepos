<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/reporting/sms_reportviewschema-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ReportViewSchema Server WMI Class

The `SMS_ReportViewSchema` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the views and columns that are available for building a report.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ReportViewSchema : SMS_BaseClass
{
      Boolean IsStringType;
      String ViewColumnName;
      String ViewName;
};
```

## Methods

The following table shows the methods in `SMS_ReportViewSchema`.

| Method | Description |
| --- | --- |
| [GetSampleValues Method in Class SMS\_ReportViewSchema](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/reporting/getsamplevalues-method-in-class-sms_reportviewschema) | Gets sample values for a report view schema. |

## Properties

`IsStringType` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the values of the column are strings.

`ViewColumnName` Data type: `String`

Access type: Read Only

Qualifiers: \[key\]

Name of a column in the view.

`ViewName` Data type: `String`

Access type: Read Only

Qualifiers: \[key\]

Name of a view.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
