<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass--createidentity-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IPxeAuthClass::CreateIdentity Method

In Configuration Manager, the `CreateIdentity` method creates a PXE certificate identity that is used in the client configuration file. This method is used to create a new self-signed certificate.

## Syntax

```
HRESULT CreateIdentity(
      BSTR FriendlyName,
      BSTR SubjectName,
      BSTR SMSID,
      VARIANT* StartTime,
      VARIANT* EndTime,
      VARIANT* Identity
);
```

#### Parameters

`FriendlyName` Data type: `BSTR`

Qualifiers: \[in\]

Friendly name of the certificate identity.

`SubjectName` Data type: `BSTR`

Qualifiers: \[in\]

Name of the certificate subject.

`SMSID` Data type: `BSTR`

Qualifiers: \[in\]

The GUID used to identify the certificate. This is the value of the SMSID property in [SMS\_CertificateInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_certificateinfo-server-wmi-class).

`StartTime` Data type: `VARIANT`

Qualifiers: \[in\]

Time when the certificate becomes valid.

`EndTime` Data type: `VARIANT`

Qualifiers: \[in\]

Time when the validity of the certificate ends.

`Identity` Data type: `VARIANT`

Qualifiers: \[out, retval\]

PXE certificate identity. Can be used with [SubmitRegistrationRecord Method in Class SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/submitregistrationrecord-method-in-class-sms_site).

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following value.

S\_OK The method succeeded.

## Remarks

## See Also

[IPxeAuthClass Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ipxeauthclass-interface) [About Operating System Deployment Site Role Configuration](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-site-role-configuration)
