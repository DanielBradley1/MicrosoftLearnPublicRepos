<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/generateprovisioningxml-method-in-class-sms_bulkenrollmentprofiles -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GenerateProvisioningXML Method in Class SMS\_BulkEnrollmentProfiles

The `ImportForProfile` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, generates provisioning data in XML format.

## Syntax

```
sint32 GenerateProvisioningXML(
     String BulkEnrollmentProfileID,
     Boolean IsEncrypted,
     String EncrytionPassword,
     String ProvisioningDataXML
);
```

#### Parameters

`BulkEnrollmentProfileID` Data type: `String`

Qualifiers: \[in\]

The ID of the bulk enrollment profile.

`IsEncrypted` Data type: `Boolean`

Qualifiers: \[in\]

`true` if the enrollment package is password-protected. The default value is `false`.

`EncrytionPassword` Data type: `String`

Qualifiers: \[in, optional\]

The password used to encrypt the enrollment package.

`ProvisioningDataXML` Data type: `String`

Qualifiers: \[out\]

The XML output that contains the provisioning data.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BulkEnrollmentProfiles Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_bulkenrollmentprofiles-server-wmi-class)
