<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getclientconfigpolicies-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetClientConfigPolicies Method in Class SMS\_TaskSequencePackage

The `GetClientConfigPolicies` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets all site-wide client configuration policies and their corresponding policy assignments.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetClientConfigPolicies(
      String PolicyXmls[],
      String PolicyAssignmentXmls[]
);
```

#### Parameters

`PolicyXmls` Data type: `String` Array

Qualifiers: \[out\]

The XML representations of all site-wide client configuration policies.

`PolicyAssignmentXmls` Data type: `String` Array

Qualifiers: \[out\]

The XML representations of all site-wide client configuration policy assignments. This parameter and `PolicyXmls` are aligned, with the nth element of one corresponding to the nth element of the other.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class)
