<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getpackagehash-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetPackageHash Method in Class SMS\_TaskSequencePackage

The `GetPackageHash` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the hash of a Configuration Manager package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetPackageHash(
      String PackageID,
      UInt32 SourceVersion,
      String Hash,
      UInt32 HashVersion
);
```

#### Parameters

`PackageID` Data type: `String`

Qualifiers: \[in\]

ID of the task sequence package.

`SourceVersion` Data type: `UInt32`

Qualifiers: \[in\]

The version of the package available at the site. This version is indicated by the `SourceVersion` property of [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class).

`Hash` Data type: `String`

Qualifiers: \[out\]

The hash for the package content.

`HashVersion` Data type: `UInt32`

Qualifiers: \[out\]

The type of the requested hash which can be one of the following values.

1 - MD5 hash

2 - SHA-1 hash

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)
