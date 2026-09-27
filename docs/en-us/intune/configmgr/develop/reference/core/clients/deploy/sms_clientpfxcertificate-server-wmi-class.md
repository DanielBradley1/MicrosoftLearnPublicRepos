<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientpfxcertificate-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ClientPfxCertificate Server WMI Class

The `SMS_ClientPfxCertificate` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that contains an imported Pfx certificate.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientPfxCertificate : SMS_BaseClass
{
    UInt32 CI_ID;
    UInt32 DeviceID;
    UInt32 IsTombstoned;
    String ProfileName;
    String Thumbprint;
    UInt32 UserItemKey;
    String UserName;
    DateTime ValidFrom;
    DateTime ValidUntil;
};
```

## Methods

The following table lists the methods in the `SMS_ClientPfxCertificate` class.

| Method | Description |
| --- | --- |
| [ImportForUser Method in Class SMS\_ClientPfxCertificate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/importforuser-method-in-class-sms_clientpfxcertificate) | Imports a certificate for a user, encrypted by using a password. |
| [DeleteForUser Method in Class SMS\_ClientPfxCertificate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/deleteforuser-method-in-class-sms_clientpfxcertificate) | Deletes a certificate for a user. |

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key\]

The unique ID of the configuration item.

`DeviceID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key\]

The ID of the device.

`IsTombstoned` Data type: `UInt32`

Access type: Read

Qualifiers: none

Specifies whether the certificate is marked for deletion.

`ProfileName` Data type: `String`

Access type: Read

Qualifiers: \[key\]

An SMS\_ConfigurationPolicy Profile unique ID.

`Thumbprint` Data type: `String`

Access type: Read

Qualifiers: \[key\]

The thumbprint for the certificate.

`UserItemKey` Data type: `UInt32`

Access type: Read

Qualifiers: \[key\]

The user item key.

`UserName` Data type: `String`

Access type: Read

Qualifiers: \[key\]

The user name.

`ValidFrom` Data type: `DateTime`

Access type: Read

Qualifiers: none

The start date for the certificate.

`ValidUntil` Data type: `DateTime`

Access type: Read

Qualifiers: none

The expiration date for the certificate.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
