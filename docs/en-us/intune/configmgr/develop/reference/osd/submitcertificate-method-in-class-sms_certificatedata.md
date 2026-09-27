<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/submitcertificate-method-in-class-sms_certificatedata -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SubmitCertificate Method in Class SMS\_CertificateData

The `SubmitCertificate` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that submits the specified certificate.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 SubmitCertificate
{
    [IN]    UInt32 CertType
    [IN]    UInt8 CertData[]
    [IN]    UInt8 Password[]
    [IN]    String Name
    [IN]    String Description
};
```

## Parameters

`CertType` Data type: `UInt32`

Qualifiers: \[id\("0"\), in\]

Required. Certificate type. Possible values are:

| Value | Certificate type |
| --- | --- |
| 1 | Windows Intune Subscription |

`CertData` Data type: `UInt8 Array`

Qualifiers: \[id\("1"\), in\]

Required. Certificate PFX data.

`Password` Data type: `UInt8 Array`

Qualifiers: \[id\("2"\), in, optional\]

Optional. Password to read the certificate PFX data.

`Name` Data type: `String`

Qualifiers: \[id\("3"\), in, optional\]

Optional. Certificate name.

`Description` Data type: `String`

Qualifiers: \[id\("4"\), in, optional\]

Optional. Certificate description.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CertificateData Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificatedata-server-wmi-class)
