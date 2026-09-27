<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aicategory -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSummary Method in Class SMS\_AICategory

The `GetSummary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, provides a summary count of all the categories, families, and tags used by Asset Intelligence.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetSummary(
     UInt32 ValidatedCategory,
     UInt32 UserDefinedCategory,
     UInt32 ValidatedFamily,
     UInt32 UserDefinedFamily,
     UInt32 UserDefinedTags
);
```

#### Parameters

`ValidatedCategory` Data type: `UInt32`

Qualifiers: \[out\]

Count of Microsoft-defined categories.

`UserDefinedCategory` Data type: `UInt32`

Qualifiers: \[out\]

Count of user-defined categories.

`ValidatedFamily` Data type: `UInt32`

Qualifiers: \[out\]

Count of Microsoft-defined families.

`UserDefinedFamily` Data type: `UInt32`

Qualifiers: \[out\]

Count of user-defined families.

`UserDefinedTags` Data type: `UInt32`

Qualifiers: \[out\]

Count of all tags defined by the user.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AICategory Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aicategory-server-wmi-class)
