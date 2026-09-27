<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencesinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequenceAppReferencesInfo Server WMI Class

The `SMS_TaskSequenceAppReferencesInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a Configuration Manager application in the task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceAppReferencesInfo : SMS_BaseClass
{
    String PackageID;
    SInt32 RefAppCI_ID;
    String RefAppModelName;
    String RefAppPackageID;
};
```

## Methods

The `SMS_TaskSequenceAppReferencesInfo` class does not define any methods.

## Properties

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Package ID of the task sequence.

`RefAppCI_ID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

CI\_ID of the referenced by task sequence application.

`RefAppModelName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The model name of the referenced by task sequence application.

`RefAppPackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Package ID of the referenced by task sequence application.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
