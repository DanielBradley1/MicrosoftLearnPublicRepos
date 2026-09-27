<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageupdatestatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImageUpdateStatus Server WMI Class

The `SMS_ImageUpdateStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents software update installation status of offline servicing image.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageUpdateStatus : SMS_BaseClass
{
    DateTime AppliedDateTime;
    SInt32 ImageIndex;
    String ImagePackageID;
    SInt32 UpdateID;
    SInt32 UpdateInstallationStatus;
    SInt32 UpdateStatus;
    String UpdateTitle;
};
```

## Methods

The `SMS_ImageUpdateStatus` class does not define any methods.

## Properties

`AppliedDateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Software update installation date.

`ImageIndex` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

Index for offline servicing image.

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID for offline servicing image.

`UpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID for software update in offline servicing image.

`UpdateInstallationStatus` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Error code for software update installation.

`UpdateStatus` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Applicability state for software update.

| Value | Update status |
| --- | --- |
| 0 | Unknown |
| 1 | Not Required |
| 2 | Installed |
| 3 | Applicable |
| 4 | Applicability check not supported |
| 5 | Installed applicability check not supported |

`UpdateTitle` Data type: `String`

Access type: Read/Write

Qualifiers: none

Display name for software update.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
