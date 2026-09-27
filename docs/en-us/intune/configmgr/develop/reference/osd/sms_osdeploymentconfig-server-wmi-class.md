<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentconfig-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_OSDeploymentConfig Server WMI Class

The `SMS_OSDeploymentConfig` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents all OSD-related constants and settings with their ADK-specific values.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentConfig : SMS_BaseClass
{
    String DeploymentKitVersion;
    String DeploymentPropertyName;
    String DeploymentPropertyValue;
};
```

## Methods

The `SMS_OSDeploymentConfig` class does not define any methods.

## Properties

`DeploymentKitVersion` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, not\_null\]

The version of the deployment kit with which this property is associated.

`DeploymentPropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, not\_null\]

The name of the property.

`DeploymentPropertyValue` Data type: `String`

Access type: Read/Write

Qualifiers: none

The value of the property.

## Remarks

Class qualifiers for this class include:

- Dynamic

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
