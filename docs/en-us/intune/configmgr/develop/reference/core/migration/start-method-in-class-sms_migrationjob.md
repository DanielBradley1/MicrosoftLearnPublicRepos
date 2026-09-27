<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/start-method-in-class-sms_migrationjob -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Start Method in Class SMS\_MigrationJob

The `Start` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, starts the migration job.

Important

This requires the Manage Migration Job right.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 Start();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MigrationJob Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationjob-server-wmi-class)
