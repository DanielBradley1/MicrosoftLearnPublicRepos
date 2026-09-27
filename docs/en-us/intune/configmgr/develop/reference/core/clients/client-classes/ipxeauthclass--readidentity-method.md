<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--readidentity-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IPxeAuthClass::ReadIdentity Method

In Configuration Manager, the `ReadIdentity` method reads a PXE certificate identity from the client configuration \(PFX\) file. The method is used in serializing a certificate from the file.

## Syntax

```
HRESULT ReadIdentity(
   BSTR FileName,
   BSTR FilePassword,
   BSTR SMSID,
   VARIANT* Identity
);
```

#### Parameters

`FileName` Data type: `BSTR`

Qualifiers: \[in\]

Name of the client configuration \(PFX\) file.

`FilePassword` Data type: `BSTR`

Qualifiers: \[in\]

Password to use for access to the client configuration file.

`SMSID` Data type: `BSTR`

Qualifiers: \[in\]

The GUID used to identify the certificate. This is the value of the SMSID property in [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`Identity` Data type: `VARIANT`

Qualifiers: \[out, retval\]

PXE certificate identity. The return value can be used with [SubmitRegistrationRecord Method in Class SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site).

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following value.

S\_OK The method succeeded.

## Remarks

## See Also

[IPxeAuthClass Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass-interface) [About Operating System Deployment Site Role Configuration](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-site-role-configuration)
