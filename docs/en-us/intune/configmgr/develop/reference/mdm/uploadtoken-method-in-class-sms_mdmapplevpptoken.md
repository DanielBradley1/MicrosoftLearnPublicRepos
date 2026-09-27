<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/uploadtoken-method-in-class-sms_mdmapplevpptoken -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UploadToken Method in Class SMS\_MDMAppleVppToken

The `UploadToken` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, uploads an Apple Volume Purchase Program \(VPP\) token to Microsoft Intune.

## Syntax

```
sint32 UploadToken(
     String TokenID,
     String VppToken,
     String OrganizationName,
     String ExpirationDate
);
```

#### Parameters

`TokenID` Data type: `String`

Qualifiers: \[in\]

The ID of the Apple VPP token.

`VppToken` Data type: `String`

Qualifiers: \[in\]

Name of the token.

`OrganizationName` Data type: `String`

Qualifiers: \[in\]

Organization name for the token.

`ExpirationDate` Data type: `String`

Qualifiers: \[in\]

Expiration date of the token.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MDMAppleVppToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmapplevpptoken-server-wmi-class)
