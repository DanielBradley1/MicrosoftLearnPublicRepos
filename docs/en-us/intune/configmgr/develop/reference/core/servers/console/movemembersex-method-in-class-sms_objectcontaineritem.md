<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/movemembersex-method-in-class-sms_objectcontaineritem -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# MoveMembersEx Method in Class SMS\_ObjectContainerItem

The `MoveMembersEx` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, moves folder items to another folder.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 MoveMembers(
     String InstanceKeys[],
     UInt32 ContainerNodeID,
     UInt32 TargetContainerNodeID,
     UInt32 ObjectTypeName,
);
```

#### Parameters

`InstanceKeys` Data type: `String` Array

Qualifiers: \[in\]

Instance keys that identify the folder items to move.

`ContainerNodeID` Data type: `UInt32`

Qualifiers: \[in\]

ID of the folder, or node, from which to copy the items.

`TargetContainerNodeID` Data type: `UInt32`

Qualifiers: \[in\]

ID of the folder, or node, to which to move the items.

`ObjectTypeName` Data type: `UInt32`

Qualifiers: \[in\]

The name of the object supported by the console folder.

## Return Value

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

An item cannot be moved to a folder of a different type. The `ObjectType` properties of [SMS\_ObjectContainerNode Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontainernode-server-wmi-class) and [SMS\_ObjectContainerItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontaineritem-server-wmi-class) can be used to determine object types.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
