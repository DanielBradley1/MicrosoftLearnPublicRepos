<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentkitsupportedplatforms-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_OSDeploymentKitSupportedPlatforms Server WMI Class

The `SMS_OSDeploymentKitSupportedPlatforms` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that maps Assessment and Deployment Kit \(ADK\) versions to supported platforms.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentKitSupportedPlatforms : SMS_SupportedPlatformsOfflineServicing
{
    String DeploymentKitVersion;
    String Name;
    String OsVersionBuild;
    String ProductType;
};
```

## Methods

The `SMS_OSDeploymentKitSupportedPlatforms` class does not define any methods.

## Properties

`DeploymentKitVersion` Data type: `String`

Access type: Read

Qualifiers: \[not\_null\]

The version of the deployment kit with which this property is associated.

`Name` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null\]

See [SMS\_SupportedPlatformsOfflineServicing Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class).

`OsVersionBuild` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null\]

See [SMS\_SupportedPlatformsOfflineServicing Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class).

`ProductType` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null\]

See [SMS\_SupportedPlatformsOfflineServicing Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatformsofflineservicing-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
