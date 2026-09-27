<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionjob-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DistributionJob Server WMI Class

The `SMS_DistributionJob` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a distribution point job.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionJob : SMS_BaseClass
{
    UInt32 Action;
    Datetime CreationTime;
    UInt32 DPID;
    UInt32 DynamicOrder;
    UInt64 JobID;
    Datetime LastUpdateTime;
    String NALPath;
    UInt32 PackageVersion;
    String PkgID;
    UInt32 RemainingSize;
    UInt32 ReStartTime;
    UInt32 RetryCount;;
    Datetime StartTime;
    UInt32 State;
    UInt64 TotalSize;
};
```

## Methods

The `SMS_DistributionJob` class does not define any methods.

## Properties

`Action` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Current job action. Possible values are:

| Value | Job action |
| --- | --- |
| 1 | DISTSRC\_ACTION\_UPDATE |
| 2 | DISTSRC\_ACTION\_ADD |
| 5 | DISTSRC\_ACTION\_CANCEL |

`CreationTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: \[read\]

Job creation time.

`DPID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Distribution point identifier.

`DynamicOrder` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Dynamic order for the job.

`JobID` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[read, key\]

Job identifier.

`LastUpdateTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: \[read\]

Last update time of the job.

`NALPath` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Distribution point NAL path.

`PackageVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Package version.

`PkgID` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Package identifier.

`RemainingSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Remaining size of the distribution job.

`ReStartTime` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Job restart time.

`RetryCount` Data type: `UIn32`

Access type: Read-only

Qualifiers: \[read\]

Retry count.

`StartTime` Data type: `Datetime`

Access type: Read-only

Qualifiers: \[read\]

Job start time.

`State` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Current job state. Possible values are:

`TotalSize` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[read\]

Date of the last status update.

| Value | Job state |
| --- | --- |
| 0 | DISTSRC\_STATE\_PENDING |
| 1 | DISTSRC\_STATE\_READY |
| 2 | DISTSRC\_STATE\_STARTED |
| 3 | DISTSRC\_STATE\_INPROGRESS |
| 4 | DISTSRC\_STATE\_PENDING\_RESTART |
| 5 | DISTSRC\_STATE\_COMPLETE |
| 6 | DISTSRC\_STATE\_FAILED |
| 7 | DISTSRC\_STATE\_CANCELLED |
| 8 | DISTSRC\_STATE\_SUSPENDED |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
