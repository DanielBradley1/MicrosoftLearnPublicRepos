<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_pxecertificateinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PXECertificateInfo Server WMI Class

The `SMS_PXECertificateInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that defines a media certificate that is registered by Configuration Manager and used by PXE clients to communicate with a management point.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_PXECertificateInfo : SMS_CertificateInfo
{
      String Certificate;
      Boolean IsApproved;
      Boolean IsBlocked;
      String IssuedTo;
      SInt32 KeyType;
      String PublicKey;
      String PXEServerName;
      String SMSID;
      String Thumbprint;
      UInt32 Type;
      DateTime ValidFrom;
      DateTime ValidUntil;
};
```

## Methods

The `SMS_PXECertificateInfo` class does not define any methods.

## Properties

`Certificate` Data type: `String`

Access type: Read/Write

Qualifiers: \[large, lazy\]

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`IsApproved` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`IsBlocked` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`IssuedTo` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`KeyType` Data type: `SInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`PublicKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`PXEServerName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the PXE server to which the PXE certificate belongs.

`SMSID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`Thumbprint` Data type: `String`

Access type: Read/Write

Qualifiers: \[Lazy\]

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`ValidFrom` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`ValidUntil` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_CertificateInfo server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class)
