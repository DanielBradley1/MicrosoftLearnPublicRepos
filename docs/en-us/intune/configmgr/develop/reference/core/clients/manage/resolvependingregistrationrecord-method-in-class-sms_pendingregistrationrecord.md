<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/resolvependingregistrationrecord-method-in-class-sms_pendingregistrationrecord -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ResolvePendingRegistrationRecord Method in Class SMS\_PendingRegistrationRecord

The `ResolvePendingRegistrationRecord` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, resolves any conflicts for the pending registration records.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 ResolvePendingRegistrationRecord(
     string SMSID,
     uint32 Action
);
```

#### Parameters

`SMSID` Data type: `String`

Qualifiers: \[in\]

Pending registration record id to use.

`Action` Data type: `UInt32`

Qualifiers: \[in\]

Action to execute on the pending registration record. Possible values are:

| Value | Description |
| --- | --- |
| 1 | Merge: Allows the record to take over the existing conflicting record. |
| 2 | New: Creates a new record for the `SMSID` resource. This resource is then issued a new `SMSID` value. |
| 3 | Reject: Creates a new record for the `SMSID` resource. This resource is then issued a new `SMSID` value, but is restricted from communicating with the Configuration Manager site. |

## Return Values

An `SInt32`data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
