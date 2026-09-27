<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlockasync-method-in-class-sms_objectlock -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RequestLockAsync Method in Class SMS\_ObjectLock

The `RequestLockAsync` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, asynchronously acquires a lock to edit global objects.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RequestLockAsync(
    string ObjectRelPath,
    boolean RequestTransfer,
    string RequestID
);
```

#### Parameters

`ObjectRelPath` Data type: `String`

Qualifiers: \[in\]

The path of the object for which the lock is requested.

`RequestTransfer` Data type: `Boolean`

Qualifiers: \[in, optional\]

If the lock is not owned by the local site, the lock request should be forwarded to the parent/child site.

`RequestID` Data type: `String`

Qualifiers: \[out\]

Unique identifier of the request.

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
