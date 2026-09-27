<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackagesitestatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CM\_UpdatePackageSiteStatus Server WMI Class

The `SMS_CM_UpdatePackageSiteStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that is used to get the update package installation status per site.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackageSiteStatus : SMS_BaseClass
{
    DateTime LastUpdateTime;
    String Name;
    String PackageGuid;
    SInt32 PrereqFlag;
    String SiteCode;
    String SiteName;
    SInt32 SiteNumber;
    String SiteServerName;
    Sint32 SiteType;
    Sint32 State;
};
```

## Methods

The following table lists the methods in the `SMS_CM_UpdatePackageSiteStatus` class.

| Method | Description |
| --- | --- |
| [UpdatePackageSiteState Method in Class SMS\_CM\_UpdatePackageSiteStatus](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/updatepackagesitestate-method-in-class-sms_cm_updatepackagesitestatus) | Updates the package installation state of the site. |

## Properties

`LastUpdateTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: none

The date and time that the state was last updated.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

The name of the update package.

`PackageGuid` Data type: `String`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

The unique identifier of the package.

`PrereqFlag` Data type: `SInt32`

Access type: Read-only

Qualifiers: \[read\]

Prerequisite flag. Possible values are: bits:

| Value | Description |
| --- | --- |
| 0x1 | Prereq only |
| 0x2 | CONTINUE\_ON\_PREREQ\_WARNING |

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

The site code.

`SiteName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

The name of the site.

`SiteNumber` Data type: `SInt32`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

The unique identifier of the site.

`SiteServerName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

The site server name.

`SiteType` Data type: `SInt32`

Access type: Read-only

Qualifiers: \[read\]

The site type.

`State` Data type: `SInt32`

Access type: Read-only

Qualifiers: none

The state of the installation.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
