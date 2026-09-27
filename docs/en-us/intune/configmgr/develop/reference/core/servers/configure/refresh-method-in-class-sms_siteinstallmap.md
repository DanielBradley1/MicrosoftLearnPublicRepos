<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/refresh-method-in-class-sms_siteinstallmap -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Refresh Method in Class SMS\_SiteInstallMap

The `Refresh` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reloads the install map from the database, which repopulates the classes.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 Refresh( );
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method is used in the rare case when a new component is added by Configuration Manager site setup and the SMS Provider is located on a remote SQL Server computer that might not be restarted. Generally it isn't necessary for your application to call this method because the SMS Provider copy of the install map will be up to date.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteInstallMap Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class)
