<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/validatenewpackagesource-method-in-class-sms_softwareupdatespackage -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# ValidateNewPackageSource Method in Class SMS\_SoftwareUpdatesPackage

The `ValidateNewPackageSource` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, validates a new package source location for a software update.

Note

All of the updates available in the old package source must be available in the new package source for validation to succeed.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ValidateNewPackageSource(  
     String PackageSource  
);  
```

#### Parameters

`PackageSource`  
Data type: `String`

Qualifiers: \[in\]

The location of the package content to verify.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method might be used when changing the package source location of a software update package due to infrastructure changes or a server failure.

This method is new in the latest version of Configuration Manager. Note that it is the only way to change the package source for an [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) object. Most other types of packages can be changed in the console, but not the software update package. The access to this package from the console is restricted.

To use this method:

1. Manually copy the package files from the old source location to the new location.
2. In your application, obtain the [SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) object for the software update.
3. Include a call to `ValidateNewPackageSource` on the package.
4. On successful return from the method, have the application change the `StoredPkgPath` property in the package to indicate the new source location.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class)  
[RefreshPkgSource Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/refreshpkgsource-method-in-class-sms_softwareupdatespackage)  
[SetSourceSite Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/setsourcesite-method-in-class-sms_softwareupdatespackage)  
[Unlock Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/unlock-method-in-class-sms_softwareupdatespackage)
