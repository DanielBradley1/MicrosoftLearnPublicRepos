<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_objectlock-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ObjectLock Server WMI Class

The `SMS_ObjectLock` abstract Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents methods for locking and unlocking global objects.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectLock : SMS_BaseClass
{
};
```

## Methods

The following table shows the methods in `SMS_ObjectLock`.

| Method | Description |
| --- | --- |
| [CancelLockRequest Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/cancellockrequest-method-in-class-sms_objectlock) | Cancels a lock request. |
| [CancelLockRequests Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/cancellockrequests-method-in-class-sms_objectlock) | Cancels multiple lock requests. |
| [CheckLockRequest Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/checklockrequest-method-in-class-sms_objectlock) | Checks a lock request. |
| [CheckLockRequests Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/checklockrequests-method-in-class-sms_objectlock) | Checks multiple lock requests. |
| [GetLockInformation Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getlockinformation-method-in-class-sms_objectlock) | Gets current lock information. |
| [ReleaseAllLocks Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/releasealllocks-method-in-class-sms_objectlock) | Releases all locks for a session. |
| [ReleaseLock Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/releaselock-method-in-class-sms_objectlock) | Releases a lock to global object. |
| [ReleaseLocks Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/releaselocks-method-in-class-sms_objectlock) | Releases locks to multiple global objects. |
| [RequestLock Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlock-method-in-class-sms_objectlock) | Synchronously acquires a lock to edit global object. |
| [RequestLockAsync Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlockasync-method-in-class-sms_objectlock) | Asynchronously acquires a lock to edit global objects. |
| [RequestLocks Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlocks-method-in-class-sms_objectlock) | Synchronously acquires a lock to edit a global object. |
| [RequestLocksAsync Method in Class SMS\_ObjectLock](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/requestlocksasync-method-in-class-sms_objectlock) | Asynchronously acquires locks to edit multiple global objects. |

## Properties

None.

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
