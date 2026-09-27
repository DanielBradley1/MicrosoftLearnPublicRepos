<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/refreshpkgsource-method-in-class-sms_softwareupdatespackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RefreshPkgSource Method in Class SMS\_SoftwareUpdatesPackage

The `RefreshPkgSource` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, refreshes the package source at all distribution points. The latest version of the package is copied to all the distribution points of the package. The source version of the package is incremented, and the package content is replicated to child sites.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RefreshPkgSource();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Using this method is the only way to force an update of the source files, other than by creating a `RefreshSchedule` value for the package. For information about the `RefreshSchedule` property, see [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) [SetSourceSite Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/setsourcesite-method-in-class-sms_softwareupdatespackage) [ValidateNewPackageSource Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage) [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class)
