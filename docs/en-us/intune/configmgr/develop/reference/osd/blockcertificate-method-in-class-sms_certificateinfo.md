<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# BlockCertificate Method in Class SMS\_CertificateInfo

The `BlockCertificate` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, blocks or unblocks the specified certificate.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 BlockCertificate(
      String SMSID,
      Boolean Blocked
);
```

#### Parameters

`SMSID` Data type: `String`

Qualifiers: \[in\]

The GUID used to identify the certificate. This identifier is defined by the `SMSID` property of [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`Blocked` Data type: `Boolean`

Qualifiers: \[in\]

`true`, by default, to block the certificate. A blocked certificate is rejected by the site database. See the Remarks section later in this topic.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

The value furnished for the `Blocked` parameter directly affects the setting of the `IsBlocked` property of [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class)
