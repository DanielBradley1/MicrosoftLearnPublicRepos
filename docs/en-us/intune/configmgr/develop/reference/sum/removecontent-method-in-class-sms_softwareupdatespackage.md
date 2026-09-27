<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RemoveContent Method in Class SMS\_SoftwareUpdatesPackage

The `RemoveContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, removes old or unnecessary content from the software updates package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RemoveContent(
     UInt32 ContentIDs[],
     Boolean bRefreshDPs
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: \[in\]

IDs of content to remove from the software updates package.

`bRefreshDPs` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true`, by default, to replicate package content to the distribution points.

## Return Values

The method returns an exception on failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

To determine the content to remove using this method, your application should use [SMS\_CIToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) [AddUpdateContent Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage) [RebuildPackage Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/rebuildpackage-method-in-class-sms_softwareupdatespackage)
