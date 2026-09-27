<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getcontenthash-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetContentHash Method in Class SMS\_TaskSequencePackage

The `GetContentHash` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the hash of specific Configuration Manager content.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetContentHash(
      UInt32 ContentID,
      UInt32 HashAlgID,
      String Hash
);
```

#### Parameters

`ContentID` Data type: `UInt32`

Qualifiers: \[in\]

ID of the content.

`HashAlgID` Data type: `UInt32`

Qualifiers: \[in\]

The ID of the cryptographic algorithm used to hash the content.

`Hash` Data type: `String`

Qualifiers: \[out\]

The hash for the content.

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
