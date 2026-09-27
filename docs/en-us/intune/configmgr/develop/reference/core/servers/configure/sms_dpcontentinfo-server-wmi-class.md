<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpcontentinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DPContentInfo Server WMI Class

The `SMS_DPContentInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that describes package information for a given distribution point.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DPContentInfo : SMS_BaseClass
{
    String Description;
    Boolean IsPredefinedPackage;
    String NALPath;
    String Name;
    String ObjectID;
    UInt32 ObjectType;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 SourceSize;
};
```

## Methods

The `SMS_DPContentInfo` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description for the package or application.

`IsPredefinedPackage` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`True` if this package is a predefined package.

`NALPath` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Distribution point NALPath.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the package or application.

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

The identifier of the package or the unique identifier of the configuration item.

`ObjectType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Object type.

| value | Object type |
| --- | --- |
| Value | Description |
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

Secured object class ID.

| Value | Object type |
| --- | --- |
| Value | Description |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifier for the package.

`SourceSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Source size of the package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
