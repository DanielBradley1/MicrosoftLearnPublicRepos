<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/releaselocks-method-in-class-sms_objectlock -->
<!-- Sitemap-Last-Modified: 2023-01-20 -->

# ReleaseLocks Method in Class SMS\_ObjectLock

The `ReleaseLocks` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, releases locks to multiple global objects.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ReleaseLocks(
    string ObjectRelPaths[]
);
```

#### Parameters

`ObjectRelPaths` Data type: `String` Array

Qualifiers: \[in\]

The paths of the objects from which to release the locks.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ObjectLock Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_objectlock-server-wmi-class)
