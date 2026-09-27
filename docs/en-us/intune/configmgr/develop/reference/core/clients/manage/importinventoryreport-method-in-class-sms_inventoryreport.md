<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/importinventoryreport-method-in-class-sms_inventoryreport -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ImportInventoryReport Method in Class SMS\_InventoryReport

The `ImportInventoryReport` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports an inventory class from the MOF file content.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 ImportInventoryReport(
     string InventoryReportID,
     uint32 ImportType,
     string MofBuffer
);
```

#### Parameters

`InventoryReportID` Data type: `String`

Qualifiers: \[in\]

Inventory report ID.

`ImportType` Data type: `UInt32`

Qualifiers: \[in\]

Import type. Possible values are:

| Value | Description |
| --- | --- |
| 1 | ClassOnly: Imports only the inventory class. This option is only available at the central site or a standalone primary site. |
| 2 | ReportOnly: Imports only the inventory report. |
| 3 | BothClassAndReport: Imports both inventory class definition and inventory report information. |

`MofBuffer` Data type: `String`

Qualifiers: \[in\]

The MOF content that contains the inventory class or report to import. This is the same format as the Configuration Manager 2007 sms\_def.mof file, or the file format that you export from inventory client settings.

## Return Values

An `SInt32`data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
