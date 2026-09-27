<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DistributionStatus Server WMI Class

The `SMS_DistributionStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that represents the status of a package that has been assigned to a distribution point.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DistributionStatus : SMS_BaseClass
{
    UInt32 Assets;
    DateTime LastUpdateDate;
    UInt32 MessageCategory;
    String ObjectID;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 Type;
};
```

## Methods

The `SMS_DistributionStatus` class doesn't define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Number of distribution points in this status.

`LastUpdateDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

Last status update date.

`MessageCategory` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

Status message category.

`ObjectID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

PackageID or ModelName.

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Secured object class ID.

| Value | Object type |
| --- | --- |
| 2 | SMS\_DistributionStatus |
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

PackageID.

`Type` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Status Type.

| Value | Status type |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | Error |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
