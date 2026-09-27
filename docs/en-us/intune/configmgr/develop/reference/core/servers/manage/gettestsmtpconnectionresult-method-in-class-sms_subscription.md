<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/gettestsmtpconnectionresult-method-in-class-sms_subscription -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetTestSmtpConnectionResult Method in Class SMS\_Subscription

The `GetTestSmtpConnectionResult` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the test SMTP connection result.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetTestSmtpConnectionResult(
     UInt32 TestID,
     UInt32 ErrorCode
);
```

#### Parameters

`TestID` Data type: `UInt32`

Qualifiers: `[in]`

Test identifier returned by `TestSmtpConnection`.

`ErrorCode` Data type: `UInt32`

Qualifiers: `[out]`

Represents the test results. Possible values are:

| Value | Error code |
| --- | --- |
| 0 | Success. |
| 1 | The test is initializing. |
| 2 | Email address formatting error. |
| 3 | Failed recipients error. |
| 4 | Connection error. |
| 5 | Other error. |
| 6 | Operation timed out. |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_Subscription server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_subscription-server-wmi-class)
