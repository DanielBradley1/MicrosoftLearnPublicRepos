<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventorydatacontext-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# InventoryDataContext Client WMI Class

In Configuration Manager, the `InventoryDataContext` class is a client Windows Management Instrumentation \(WMI\) class that represents the WMI context qualifiers to be used with inventory client agent WMI queries built from [InventoryDataItem Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventorydataitem-client-wmi-class) objects. Typically, dynamic instance providers do not require context qualifiers.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class InventoryDataContext : SMS_InventoryAgent_EmbeddedObject
{
    String Name;
    String Type;
    String Value[];
};
```

## Methods

The `InventoryDataContext` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[realkey\]

Name of the context qualifier.

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: None

String representation of the WMI variant data type for the context qualifier \(for example, 3 for integer and 8200 for string array\).

`Value` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Context qualifier value, consistent with the specified data type.

## Remarks

This class allows a generic method to specify context qualifiers for a WMI class query when they are needed. For example, the File System Inventory provider allows context qualifiers for specifying an amount of time to delay between back-to-back file operations. If no context qualifier is specified, there is no delay or throttling of scanning files on the system disk.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Inventory Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventory-agent-client-wmi-classes) [InventoryDataItem Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventorydataitem-client-wmi-class) [FileSystemFile Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/filesystemfile-client-wmi-class)
