<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_ch_evalresult-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CH\_EvalResult Server WMI Class

The `SMS_CH_EvalResult` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents client evaluation results.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CH_EvalResult : SMS_BaseClass
{
    DateTime EvalTime;
    String HealthCheckDescription;
    String HealthCheckGUID;
    UInt32 ResourceID;
    UInt32 Result;
    UInt32 ResultCode;
    String ResultDetail;
    UInt32 ResultType;
};
```

## Methods

The `SMS_CH_EvalResult` class does not define any methods.

## Properties

`EvalTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Evaluation time.

`HealthCheckDescription` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Health Check description.

`HealthCheckGUID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Health check GUID.

`ResourceID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Unique Configuration Manager-supplied ID for the resource.

`Result` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Evaluation result.

`ResultCode` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Result code.

`ResultDetail` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Result detail.

`ResultType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Result type.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
