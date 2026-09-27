<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequenceappreferencedps-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequenceAppReferenceDps Server WMI Class

The `SMS_TaskSequenceAppReferenceDps` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a distribution point to which a Configuration Manager application in the task sequence is distributed.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequenceAppReferenceDps :
{
    String Hash;
    String PackageID;
    String ServerNALPath;
    String SiteCode;
    UInt32 SourceVersion;
    String TaskSequenceID;
};
```

## Methods

The `SMS_TaskSequenceAppReferenceDps` class does not define any methods.

## Properties

`Hash` Data type: `String`

Access type: Read/Write

Qualifiers: none

Hash for application.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Package ID for application.

`ServerNALPath` Data type: `String`

Access type: Read/Write

Qualifiers: none

NALPath for distribution point.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Site code for distribution point.

`SourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Source version for application.

`TaskSequenceID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID for task sequence package.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
