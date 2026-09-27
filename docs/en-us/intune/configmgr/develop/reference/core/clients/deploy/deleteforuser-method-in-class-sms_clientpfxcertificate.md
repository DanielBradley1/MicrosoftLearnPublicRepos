<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/deleteforuser-method-in-class-sms_clientpfxcertificate -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DeleteForUser Method in Class SMS\_ClientPfxCertificate

The `DeleteForUse` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, deletes a certificate for a user.

## Syntax

```
 sint32 DeleteForUser(
     String ProfileName,
     String UserName,
     String Thumbprint
);
```

#### Parameters

`ProfileName` Data type: `String`

Qualifiers: \[in\]

The profile name.

`UserName` Data type: `String`

Qualifiers: \[in\]

The user name.

`Thumbprint` Data type: `String`

Qualifiers: \[in\]

The thumbprint for the certificate.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ClientPfxCertificate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientpfxcertificate-server-wmi-class)
