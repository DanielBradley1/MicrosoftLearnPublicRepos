<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_packageinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_PackageInfo Server WMI Class

The `SMS_TaskSequence_PackageInfo` Windows Management Instrumentation \(WMI\) class is an SMS provider server class, in Configuration Manager, that represents information about an operating system deployment task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_PackageInfo
{
    String Name;
    String PackageId;
    UInt32 PkgType;
    UInt32 Size;
};
```

## Methods

The `SMS_TaskSequence_PackageInfo` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

The name of the package.

`PackageId` Data type: `String`

Access type: Read/Write

Qualifiers: None

The ID of the package.

`PkgType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The package type.

`Size` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The size of the package, in kilobytes.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
