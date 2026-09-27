<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addcontent-method-in-class-sms_contentpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddContent Method in Class SMS\_ContentPackage

The `AddContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds content to the [SMS\_ContentPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class) content package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 AddContent (
     string ContentID[],
     uint32 ContentVersion[]
     string ContentSource[],
     uint32 ContentFlags[]
     uint32 ContentType[],
     string RelatedContentID[]
);
```

#### Parameters

`ContentID` Data type: `string` Array

Qualifiers: `[in]`

Identifier of the content.

`ContentVersion` Data type: `UInt32` Array

Qualifiers: `[in]`

Version of the content.

`ContentSource` Data type: `String` Array

Qualifiers: `[in]`

Specifies the source location where content files are stored.

`ContentFlags` Data type: `UInt32` Array

Qualifiers: `[in]`

This specifies additional attributes for the content instance.

| Value | Content flag |
| --- | --- |
| 8 | DOWNLOAD\_ON\_DEMAND\_FROM\_LOCAL\_DP |
| 12 | DOWNLOAD\_FROM\_LOCAL\_DISPPOINT |
| 13 | DOWNLOAD\_LOCAL\_PARTIALDOWNLOADTOLOCAL |
| 14 | DOWNLOAD\_FROM\_REMOTE\_DISPPOINT |
| 15 | DOWNLOAD\_REMOTE\_PARTIALDOWNLOADTOLOCAL |
| 16 | DOWNLOAD\_ENABLE\_PEER\_CACHING |
| 17 | DP\_NO\_FALLBACK\_UNPROTECTED |
| 24 | DO\_NOT\_DOWNLOAD |
| 25 | PERSIST\_IN\_CACHE |

`ContentType` Data type: `UInt32` Array

Qualifiers: `[in]`

Specifies the type of content.

`RelatedContentID` Data type: `string` Array

Qualifiers: `[in]`

Specifies the related content associated with this content.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

The input parameters are a parallel array for each content element.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
