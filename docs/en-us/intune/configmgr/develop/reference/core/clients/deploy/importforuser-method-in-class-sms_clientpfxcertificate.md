<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/importforuser-method-in-class-sms_clientpfxcertificate -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ImportForUser Method in Class SMS\_ClientPfxCertificate

The `ImportForUser` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports a certificate for a user, encrypted by using a password.

## Syntax

```
sint32 ImportForUser(
     String ProfileName,
     String UserName,
     String EncryptedPfxBlob,
     String Password
);
```

#### Parameters

`ProfileName` Data type: `String`

Qualifiers: \[in\]

The profile name.

`UserName` Data type: `String`

Qualifiers: \[in\]

The user name.

`EncryptedPfxBlob` Data type: `String`

Qualifiers: \[in\]

The encrypted blob.

`Password` Data type: `String`

Qualifiers: \[in\]

The password used to encrypt the certificate.

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
