<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/checklockrequest-method-in-class-sms_objectlock -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CheckLockRequest Method in Class SMS\_ObjectLock

The `CheckLockRequest` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, checks a lock request.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 CheckLockRequest(
    string RequestID,
    uint32 Timeout,
    uint32 RequestState,
    uint32 LockState,
    string AssignedUser,
    string AssignedObjectLockContext,
    string AssignedMachine,
    string AssignedSiteCode,
    datetime AssignedTimeUTC
);
```

#### Parameters

`RequestID` Data type: `String`

Qualifiers: \[in, out\]

Unique identifier of the request.

`Timeout` Data type: `UInt32`

Qualifiers: \[in, optional\]

Seconds to wait for lock request response.

`RequestState` Data type: `UInt32`

Qualifiers: \[out\]

The state of the lock request. Possible values are:

| Value | Request state |
| --- | --- |
| 0 | Unknown |
| 2 | Requested |
| 3 | RequestCanceled |
| 4 | ResponseReceived |
| 10 | Granted |
| 11 | GrantedAfterTimeout |
| 12 | GrantedLockWasOrphaned |
| 20 | DeniedLockAlreadyAssigned |
| 21 | DeniedInvalidObjectVersion |
| 22 | DeniedLockNotFound |
| 23 | DeniedLockNotLocal |
| 24 | DeniedRequestTimedOut |
| 50 | Error |
| 52 | ErrorRequestNotFound |
| 53 | ErrorRequestTimedOut |

`LockState` Data type: `UInt32`

Qualifiers: \[out\]

Indicates the current state of the requested lock. Possible values are:

| Value | Lock state |
| --- | --- |
| 0 | Unassigned |
| 1 | Assigned |
| 2 | Requested |
| 3 | PendingAssignment |
| 4 | TimedOut |
| 5 | NotFound |

`AssignedUser` Data type: `String`

Qualifiers: \[out\]

Indicates the currently assigned user of the requested lock.

`AssignedObjectLockContext` Data type: `String`

Qualifiers: \[out\]

Indicates the unique string identifier of the requested lock.

`AssignedMachine` Data type: `String`

Qualifiers: \[out\]

Indicates ObjectLockContext the lock is currently assigned to.

`AssignedSiteCode` Data type: `String`

Qualifiers: \[out\]

Indicates the current site of the requested lock.

`AssignedTimeUTC` Data type: `DateTime`

Qualifiers: \[out\]

Indicates the time at which the requested lock was assigned.

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
