<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/approve-method-in-class-sms_userapplicationrequest -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Approve Method in Class SMS\_UserApplicationRequest

The `Approve` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, approves user application requests.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 Approve(
     string Comments
);
```

#### Parameters

`Comments` Data type: `String` Array

Qualifiers: \[in, SizeLimit\("2000"\)\]

Comments regarding the approval of the application request.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_UserApplicationRequest Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_userapplicationrequest-server-wmi-class)
