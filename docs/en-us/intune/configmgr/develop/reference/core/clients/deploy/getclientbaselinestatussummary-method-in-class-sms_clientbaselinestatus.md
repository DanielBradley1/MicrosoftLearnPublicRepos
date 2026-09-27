<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/getclientbaselinestatussummary-method-in-class-sms_clientbaselinestatus -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetClientBaselineStatusSummary Method in Class SMS\_ClientBaselineStatus

The `GetClientBaselineStatusSummary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets baseline status summary information by `BaselineType` and `CollectionID`.

## Syntax

```
sint32 GetClientBaselineStatusSummary(
     UInt32 BaselineType,
     String CollectionID,
     UInt32 Total,
     UInt32 Compliant,
     UInt32 InProgress,
     UInt32 NotCompliant,
     UInt32 CriticalError
);
```

#### Parameters

`BaselineType` Data type: `uint32`

Qualifiers: \[in\]

The client baseline type. Possible values are:

| Value | Client baseline type |
| --- | --- |
| 1 | Production |
| 2 | Staging |

`CollectionID` Data type: `String`

Qualifiers: \[in\]

The collection for which you want to get the baseline status summary.

`Total` Data type: `uint32`

Qualifiers: \[out\]

The total number of clients in the specified collection.

`Compliant` Data type: `uint32`

Qualifiers: \[out\]

The number of clients in the specified collection that are compliant with the baseline.

`InProgress` Data type: `uint32`

Qualifiers: \[out\]

The number of clients in the specified collection for which setup is in progress.

`NotCompliant` Data type: `uint32`

Qualifiers: \[out\]

The number of clients in the specified collection that are not compliant.

`CriticalError` Data type: `uint32`

Qualifiers: \[out\]

The number of clients in the specified collection that have a critical error.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ClientBaselineStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientbaselinestatus-server-wmi-class)
