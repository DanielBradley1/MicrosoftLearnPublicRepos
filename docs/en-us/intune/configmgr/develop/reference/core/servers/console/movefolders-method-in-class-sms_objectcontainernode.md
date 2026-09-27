<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/movefolders-method-in-class-sms_objectcontainernode -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# MoveFolders Method in Class SMS\_ObjectContainerNode

The `MoveFolders` Windows Management \(WMI\) class method, in Configuration Manager, moves folders to another folder location.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 MoveFolders(
      UInt32 ContainerNodeIDs[],
      UInt32 TargetContainerNodeID,
);
```

#### Parameters

`ContainerNodeIDs` Data type: `UInt32` Array

Qualifiers: \[in\]

IDs of the folders, or nodes, to move.

`TargetContainerNodeID` Data type: `UInt32`

Qualifiers: \[in\]

The ID for the destination folder, or node.

## Return Value

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ObjectContainerNode Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontainernode-server-wmi-class)
