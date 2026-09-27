<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclass-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_InventoryClass Server WMI Class

The `SMS_InventoryClass` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents inventory classes that exist in the system.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryClass :
{
    String ClassName;
    Boolean IsDeletable;
    String Namespace;
    InventoryClassProperty Properties[];
    String SMSClassID;
    String SMSContext;
    String SMSDeviceUri;
    String SMSGroupName;
};
```

## Methods

The following table lists the methods in the `SMS_InventoryClass` class.

| Method | Description |
| --- | --- |
| GetInventoryClassesFromMof Method in Class SMS\_InventoryClass | For internal use only. |

## Properties

`ClassName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

The WMI name of the inventory class.

`IsDeletable` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

For internal use only.

`Namespace` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

The WMI namespace.

`Properties` Data type: `Object Array`

Access type: Read/Write

Qualifiers: none

The properties of this class.

`SMSClassID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

The Class ID that will be used to generate the database table, view and the UI SDK class.

`SMSContext` Data type: `String`

Access type: Read/Write

Qualifiers: none

SMS contexts in XML format. This can support multiple contexts.

`SMSDeviceUri` Data type: `String`

Access type: Read/Write

Qualifiers: none

SMS device URI in XML format. This could support multiple device URIs.

`SMSGroupName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

The default class name displayed in the MOF editor and Resource Explorer, if no localized resources are provided.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
