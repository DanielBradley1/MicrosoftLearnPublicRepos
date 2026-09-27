<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_installeddeploymenttype-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_InstalledDeploymentType Client WMI Class

The `CCM_InstalledDeploymentType` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an installed deployment type.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_InstalledDeploymentType :
{
    String Id;
    String Revision;
};
```

## Methods

The `CCM_InstalledDeploymentType` class does not define any methods.

## Properties

`Id` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Identifier.

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Revision.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
