<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymenttypelicenseassociation-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DeploymentTypeLicenseAssociation Server WMI Class

The `SMS_DeploymentTypeLicenseAssociation` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a license association for a deployment type.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DeploymentTypeLicenseAssociation : SMS_BaseClass
{
    UInt32 ID;
    String LicenseID;
    String DTModelName;
    Boolean IsEnabled;
};
```

## Methods

The following table lists the methods in the `SMS_DeploymentTypeLicenseAssociation` class.

| Method | Description |
| --- | --- |
| [AddLicense Method in Class SMS\_DeploymentTypeLicenseAssociation](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/addlicense-method-in-class-sms_deploymenttypelicenseassociation) | Adds license information to an application deployment type. |

## Properties

`ID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key\]

The ID of the deployment type.

`LicenseID` Data type: `String`

Access type: Read

Qualifiers: none

The ID of the license.

`DTModelName` Data type: `String`

Access type: Read

Qualifiers: none

The deployment type model name.

`IsEnabled` Data type: `Boolean`

Access type: Read

Qualifiers: none

Indicates whether the association is enabled.

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
