<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SubmitRegistrationRecord Method in Class SMS\_Site

The `SubmitRegistrationRecord` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, submits a registration record.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SubmitRegistrationRecord(
     String SMSID,
     String Certificate,
     String CertificatePFX,
     SInt32 Type,
     String ServerName,
     SInt32 UdaSetting,
     SInt32 IssuedCert
);
```

#### Parameters

`SMSID` Data type: `String`

Qualifiers: \[in\]

The GUID used to identify the certificate. This is the value of the `SMSID` property in [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`Certificate` Data type: `String`

Qualifiers: \[in\]

Hexadecimal-encoded certificate.

`CertificatePFX` Data type: `String`

Qualifiers: \[in, optional\]

Hexadecimal-encoded private key for PFX file containing the certificate. The default value is "".

`Type` Data type: `SInt32`

Qualifiers: \[in, optional\]

The type of certificate. Possible values are defined for the `Type` property of [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class). The default value for this parameter is BootMedia \(1\).

`ServerNam` Data type: `String`

Qualifiers: \[in, optional\]

Name used to identify the server.

`UdaSetting` Data type: `SInt32`

Qualifiers: \[in, optional\]

UdaSetting. The default value for this parameter is Disabled \(0\).

| Value | UdaSetting |
| --- | --- |
| 0 | Disabled |
| 1 | Pending |
| 2 | Auto |

`IssuedCert` Data type: `SInt32`

Qualifiers: \[in, optional\]

IssuedCert. . The default value for this parameter is 1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) [ImportMachineEntry Method in Class SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/importmachineentry-method-in-class-sms_site) [IsUsedCert Method in Class SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/isusedcert-method-in-class-sms_site) [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class)
