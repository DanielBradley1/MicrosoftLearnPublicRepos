<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageupdatestatusview-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImageUpdateStatusView Server WMI Class

The `SMS_ImageUpdateStatusView` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents software update information that is used by offline servicing image.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageUpdateStatusView : SMS_BaseClass
{
    SInt32 ErrorCode;
    SInt32 ImageIndex;
    String ImagePackageID;
    String PackageDescription;
    String PackageName;
    SInt32 UpdateID;
};
```

## Methods

The `SMS_ImageUpdateStatusView` class does not define any methods.

## Properties

`ErrorCode` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Error code for software update installation.

`ImageIndex` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

Index for offline servicing image.

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID for offline servicing image.

`PackageDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for offline servicing image.

`PackageName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name for offline servicing image.

`UpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID for software update.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
