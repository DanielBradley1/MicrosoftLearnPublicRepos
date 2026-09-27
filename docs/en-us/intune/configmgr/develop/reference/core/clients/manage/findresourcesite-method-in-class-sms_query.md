<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/findresourcesite-method-in-class-sms_query -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# FindResourceSite Method in Class SMS\_Query

The `FindResourceSite` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets site code information for resources from SQL.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 FindResourceSite(
   Boolean IncludeSubCollections,
   String SiteCode[],
   UInt32 ResourceNumber[]
);
```

#### Parameters

`IncludeSubCollections` Data type: `Boolean`

Qualifiers: \[in, optional\]

`true` if subcollections should be included. The default value is `false`.

`SiteCode` Data type: `String` Array

Qualifiers: \[out\]

Site code of the Configuration Manager site.

`ResourceNumber` Data type: `UInt32` Array

Qualifiers: \[out\]

The resource number.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Query Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class)
