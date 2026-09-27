<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/retrycontentreplication-method-in-class-sms_cm_updatepackages -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RetryContentReplication Method in Class SMS\_CM\_UpdatePackages

The `RetryContentReplication` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, triggers DistMgr to copy content from the source to the content library.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RetryContentReplication(
     UInt32 ForceRetry
);
```

#### Parameters

`ForceRetry` Data type: `UInt32`

Qualifiers: \[in, optional\]

Flag to force a retry. 1 to force a retry; otherwise 0 or `null`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CM\_UpdatePackages Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackages-server-wmi-class)
