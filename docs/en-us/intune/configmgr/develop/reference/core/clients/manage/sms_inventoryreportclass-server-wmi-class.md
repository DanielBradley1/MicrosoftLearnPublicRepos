<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryreportclass-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_InventoryReportClass Server WMI Class

The `SMS_InventoryReportClass` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class embedded in `SMS_InventoryReport` that represents the classes that are enabled to be collected in this inventory report.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryReportClass :
{
    String Filter;
    String ReportProperties[];
    String SMSClassID;
    UInt32 Timeout;
};
```

## Methods

The `SMS_InventoryReportClass` class doesn't define any methods.

## Properties

`Filter` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`ReportProperties` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

The property name in this class to collect.

`SMSClassID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

The class ID that uniquely identifies this class.

`Timeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

The timeout for the query.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
