<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddUpdateContent Method in Class SMS\_SoftwareUpdatesPackage

The `AddUpdateContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, downloads content to a software update package and replicates the content to distribution points.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddUpdateContent(
     UInt32 ContentIDs[],
     String ContentSourcePath[],
     Boolean bRefreshDPs
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: \[in\]

IDs of contents to add to the software updates package.

`ContentSourcePath` Data type: `String` Array

Qualifiers: \[in\]

The source path where the content files are located.

`bRefreshDPs` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` \(default\) to replicate package content to the distribution points.

## Return Values

The method returns an exception on failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method first creates the [SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) object and then adds the indicated content. Your application can use [SMS\_CIToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class) and [SMS\_CIContentFiles Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class) to determine the content.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) [SMS\_CIToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class) [SMS\_CIContentFiles Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class) [RebuildPackage Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/rebuildpackage-method-in-class-sms_softwareupdatespackage) [RemoveContent Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage)
