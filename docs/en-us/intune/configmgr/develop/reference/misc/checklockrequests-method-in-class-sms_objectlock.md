<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/checklockrequests-method-in-class-sms_objectlock -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CheckLockRequests Method in Class SMS\_ObjectLock

The `CheckLockRequests` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, checks multiple lock requests.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CheckLockRequests(
    string RequestIDs[],
    uint32 Timeout,
    SMS_ObjectLockRequest ObjectLockRequests[]
);
```

#### Parameters

`RequestIDs` Data type: `String` Array

Qualifiers: \[in\]

Array of unique identifiers of the request.

`Timeout` Data type: `UInt32`

Qualifiers: \[in, optional\]

Seconds to wait for lock request response.

`ObjectLockRequests` Data type: `SMS_ObjectLockRequest` Array

Qualifiers: \[out\]

A WMI class that represents object lock request information.

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
