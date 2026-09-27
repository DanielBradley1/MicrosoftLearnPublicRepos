<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontaineritem-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-04-22 -->

# SMS\_ObjectContainerItem Server WMI Class

The `SMS_ObjectContainerItem` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that contains information about a Configuration Manager console folder item.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectContainerItem : SMS_BaseClass
{
    UInt32 ContainerNodeID;
    String InstanceKey;
    String MemberGuid;
    UInt32 MemberID;
    UInt32 ObjectType;
    String ObjectTypeName;
    String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_ObjectContainerItem` class.

| Method | Description |
| --- | --- |
| [MoveMembers Method in Class SMS\_ObjectContainerItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/movemembers-method-in-class-sms_objectcontaineritem) | Moves one or more folder items to another folder. |
| [MoveMembersEx Method in Class SMS\_ObjectContainerItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/movemembersex-method-in-class-sms_objectcontaineritem) | Moves one or more folder items to another folder. |

## Properties

`ContainerNodeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Not\_null\]

The unique ID of the folder.

`InstanceKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_null\]

The name of the folder.

`MemberGuid` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The guid of the relation.

`MemberID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key, Not\_null\]

The unique ID of the relation.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[deprecated, enumeration, read\]

The type of the folder. Possible values are listed below.

| Value | Object type |
| --- | --- |
| 2 | TYPE\_PACKAGE |
| 3 | TYPE\_ADVERTISEMENT |
| 7 | TYPE\_QUERY |
| 8 | TYPE\_REPORT |
| 9 | TYPE\_METEREDPRODUCTRULE |
| 11 | TYPE\_CONFIGURATIONITEM |
| 14 | TYPE\_OSINSTALLPACKAGE |
| 17 | TYPE\_STATEMIGRATION |
| 18 | TYPE\_IMAGEPACKAGE |
| 19 | TYPE\_BOOTIMAGEPACKAGE |
| 20 | TYPE\_TASKSEQUENCEPACKAGE |
| 21 | TYPE\_DEVICESETTINGPACKAGE |
| 23 | TYPE\_DRIVERPACKAGE |
| 25 | TYPE\_DRIVER |
| 1011 | TYPE\_SOFTWAREUPDATE |
| 2011 | TYPE\_CONFIGURATIONBASELINE |
| 5000 | TYPE\_DEVICE\_COLLECTION |
| 5001 | TYPE\_USER\_COLLECTION |

`ObjectTypeName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The WMI Class Name of the object. Example SMS\_Package. This will take effect if the ObjectType is 0 or null.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The sitecode of the site that the relation was originally created from.

## Remarks

When attempting to move an item from a root node such as a user collection or device collection, the item doesn't exist as an SMS\_ObjectContainerItem. As such a new instance will need to be created instead.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
