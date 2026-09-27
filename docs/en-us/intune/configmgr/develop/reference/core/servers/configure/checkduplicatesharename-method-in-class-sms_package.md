<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/checkduplicatesharename-method-in-class-sms_package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CheckDuplicateShareName Method in Class SMS\_Package

The `CheckDuplicateShareName` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, determines if the specified share name has been used by another package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CheckDuplicateShareName(
     String ShareName,
     String PackageID,
     Boolean IsDuplicated,
      String DupPkgName,
     String DupPkgID,
     SInt32 DupPkgType
);
```

#### Parameters

`ShareName` Data type: `String`

Qualifiers: \[in\]

Share name defined for the package.

`PackageID` Data type: `String`

Qualifiers: \[in\]

ID of the package to which to add the share specified by `ShareName`.

`IsDuplicated` Data type: `Boolean`

Qualifiers: \[out\]

`true` if the share specified by `ShareName` has been used by another package.

`DupPkgName` Data type: `String`

Qualifiers: \[out\]

Name of the package using the share specified by `ShareName`.

`DupPkgID` Data type: `String`

Qualifiers: \[out\]

ID of the other package using the share specified by `ShareName`.

`DupPkgType` Data type: `SInt32`

Qualifiers: \[out\]

Type of package for which the share specified by `ShareName` is duplicated. Possible values are defined for the `PackageType` property of [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class). The default value is 1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class)
