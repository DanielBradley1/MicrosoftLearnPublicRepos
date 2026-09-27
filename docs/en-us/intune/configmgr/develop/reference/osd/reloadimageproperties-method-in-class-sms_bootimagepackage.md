<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ReloadImageProperties Method in Class SMS\_BootImagePackage

The `ReloadImageProperties` Windows Management Instrumentation WMI class method, in Configuration Manager, reloads image metadata from a boot image source .wim file and synchronizes the metadata with the database.

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

The application uses this method if the administrator changes the boot image source .wim file outside of the Configuration Manager console. The application should:

1. Establish a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Obtain the [SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) object to update.
3. Call `ReloadImageProperties`.
4. Commit the `SMS_BootImagePackage` object.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) [UpdateImage Method in Class SMS\_BootImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/updateimage-method-in-class-sms_bootimagepackage)
