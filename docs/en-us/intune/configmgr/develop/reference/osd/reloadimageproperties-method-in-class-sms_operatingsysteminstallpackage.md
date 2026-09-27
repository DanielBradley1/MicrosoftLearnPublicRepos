<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ReloadImageProperties Method in Class SMS\_OperatingSystemInstallPackage

The `ReloadImageProperties` Windows Management Instrumentation WMI class method, in Configuration Manager, reloads metadata from the source .wim file and synchronizes the metadata with the database.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ReloadImageProperties();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Your application uses this method to update the .wim file associated with the operating system install package. The update is based on the location defined in the `PkgSourcePath` property of [SMS\_OperatingSystemInstallPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class).

The application must:

1. Establish a connection to the SMS Provider. For more information, see About the SMS Provider in Configuration Manager.
2. Get the `SMS_OperatingSystemInstallPackage` object to update.
3. Call the `ReloadImageProperties` method.
4. Commit the `SMS_OperatingSystemInstallPackage` object.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_OperatingSystemInstallPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class) [GetImageProperties Method in Class SMS\_OperatingSystemInstallPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_operatingsysteminstallpackage)
