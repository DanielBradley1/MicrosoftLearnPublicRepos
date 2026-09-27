<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlocksasync-method-in-class-sms_objectlock -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RequestLocksAsync Method in Class SMS\_ObjectLock

The `RequestLocksAsync` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, asynchronously acquires locks to edit multiple global objects.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RequestLocksAsync(
    string ObjectRelPath[],
    boolean RequestTransfer,
    SMS_ObjectLockRequest ObjectLockRequests[]
);
```

#### Parameters

`ObjectRelPath` Data type: `String` Array

Qualifiers: \[in\]

The paths of the objects for which the locks are requested. `RequestTransfer` Data type: `Boolean`

Qualifiers: \[in, optional\]

If the lock is not owned by the local site, the lock request should be forwarded to the parent/child site.

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
