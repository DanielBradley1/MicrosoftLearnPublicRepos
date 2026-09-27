<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/importforprofile-method-in-class-sms_mdmbulkenrollmentpackages -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ImportForProfile Method in Class SMS\_MDMBulkEnrollmentPackages

The `ImportForProfile` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports an On-Premises Mobile Device Management \(MDM\) bulk enrollment package for a profile.

## Syntax

```
sint32 ImportForProfile(
     String ProfileGUID,
     String CertificateGUID,
     String PackageName,
     String Certificate
);
```

#### Parameters

`ProfileGUID` Data type: `String`

Qualifiers: \[in\]

The GUID of the profile.

`CertificateGUID` Data type: `String`

Qualifiers: \[in\]

The GUID of the certificate.

`PackageName` Data type: `String`

Qualifiers: \[in\]

Package name.

`Certificate` Data type: `String`

Qualifiers: \[in\]

The root certificate.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MDMBulkEnrollmentPackages Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmbulkenrollmentpackages-server-wmi-class)
