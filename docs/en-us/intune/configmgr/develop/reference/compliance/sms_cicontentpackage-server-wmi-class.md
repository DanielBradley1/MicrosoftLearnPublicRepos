<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_cicontentpackage-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIContentPackage Server WMI Class

The `SMS_CIContentPackage` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, represents the relationship between configuration item and associated content to `SMS Package` where the binary content is packaged and distributed.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIContentPackage : SMS_BaseClass
{
    UInt32 CI_ID;
    UInt32 CI_SecuredTypeID;
    String CI_UniqueID;
    String ModelName;
    String PackageID;
};
```

## Methods

The `SMS_CIContentPackage` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`CI_SecuredTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

CI\_SecuredTypeID is the associated RBAC security object type, depending on which object content \(Application, Software Update and so on\) is part of this package.

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

[SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
