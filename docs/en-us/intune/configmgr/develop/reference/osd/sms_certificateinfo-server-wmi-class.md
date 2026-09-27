<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CertificateInfo Server WMI Class

The `SMS_CertificateInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that defines a media certificate registered by Configuration Manager and used by client computers to communicate with a management point.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CertificateInfo : SMS_BaseClass
{
      String Certificate;
      Boolean IsApproved;
      Boolean IsBlocked;
      String IssuedTo;
      SInt32 KeyType;
      String PublicKey;
      String SMSID;
      String Thumbprint;
      UInt32 Type;
      DateTime ValidFrom;
      DateTime ValidUntil;
};
```

## Methods

The following table shows the methods in `SMS_CertificateInfo`.

| Name | Description |
| --- | --- |
| [BlockCertificate Method in Class SMS\_CertificateInfo](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo) | Blocks or unblocks the specified certificate. |

## Properties

`Certificate` Data type: `String`

Access type: Read/Write

Qualifiers: \[large, lazy\]

The certification content.

`IsApproved` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the certificate is approved.

`IsBlocked` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the certificate is blocked. A blocked certificate is rejected by the site database. See the [BlockCertificate Method in Class SMS\_CertificateInfo](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo).

`IssuedTo` Data type: `String`

Access type: Read/Write

Qualifiers: None

The identity of the client.

`KeyType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: None

The public key type for the certificate. Possible values are:

| Value | Key type |
| --- | --- |
| 1 | self-sign |
| 2 | issued |

`PublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

Public key of the certificate, which reflects the globally unique SHA-1 hash thumbprint indicated by the `Thumbprint` property.

`SMSID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

The GUID used to identify the certificate.

`Thumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: \[Lazy\]

Hash value of the certificate.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The type of certificate. Possible values are:

| Value | Certificate type |
| --- | --- |
| 1 | Boot Media |
| 2 | PXE |
| 3 | ISVProxy |

`ValidFrom` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the certificate becomes effective.

`ValidUntil` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the certificate expires.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[BlockCertificate Method in Class SMS\_CertificateInfo](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/blockcertificate-method-in-class-sms_certificateinfo) [SMS\_PXECertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_pxecertificateinfo-server-wmi-class)
