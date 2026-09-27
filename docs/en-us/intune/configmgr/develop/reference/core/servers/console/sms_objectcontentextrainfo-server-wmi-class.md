<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontentextrainfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ObjectContentExtraInfo Server WMI Class

The `SMS_ObjectContentExtraInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Application or Package Content Information.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ObjectContentExtraInfo : SMS_BaseClass
{
    DateTime DateCreated;
    String Description;
    UInt32 FeatureType;
    DateTime LastUpdateDate;
    UInt32 NumberErrors;
    UInt32 NumberInProgress;
    UInt32 NumberSuccess;
    UInt32 NumberUnknown;
    String ObjectID;
    UInt32 ObjectType;
    UInt32 ObjectTypeID;
    String PackageID;
    String SoftwareName;
    String SourceSite;
    UInt32 SourceSize;
    UInt32 SourceVersion;
    UInt32 Targeted;
};
```

## Methods

The `SMS_ObjectContentExtraInfo` class does not define any methods.

## Properties

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

Package creation time.

`Description` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Description for the package or application.

`FeatureType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Feature ID property for monitoring. The default value is 8.

`LastUpdateDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

Package last updated time.

`NumberErrors` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of failed distribution point.

`NumberInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of pending distribution point.

`NumberSuccess` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of distribution point which was successfully deployed.

`NumberUnknown` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of distribution point with unknown state.

`ObjectID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

PackageID or ModelName.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Object type. Possible values are listed below.

| Value | Object type |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | APPLICATION |

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Secured object class ID. Possible values are listed below.

| Value | Object type ID |
| --- | --- |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 21 | SMS\_DeviceSettingPackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Package ID.

`SoftwareName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the package or application.

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Package source site.

`SourceSize` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Package source size.

`SourceVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Package source version.

`Targeted` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of targeted distribution point.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
