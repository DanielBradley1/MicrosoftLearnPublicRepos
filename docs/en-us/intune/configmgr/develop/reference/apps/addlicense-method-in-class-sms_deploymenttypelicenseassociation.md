<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/addlicense-method-in-class-sms_deploymenttypelicenseassociation -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddLicense Method in Class SMS\_DeploymentTypeLicenseAssociation

The `AddLicense` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds license information to an application deployment type.

## Syntax

```
sint32 AddLicense (
     [in] string LicenseID,
     [in] string LicenseBlob,
     [in] string ModelName
);
```

#### Parameters

`LicenseID` Data type: `String`

Qualifiers: \[in\]

The ID of the license.

`LicenseBlob` Data type: `String`

Qualifiers: \[in\]

The license blob.

`ModelName` Data type: `String`

Qualifiers: \[in\]

The model name of the deployment type.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_DeploymentTypeLicenseAssociation Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymenttypelicenseassociation-server-wmi-class)
