<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackdetailedsitestatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# SMS\_CM\_UpdatePackDetailedSiteStatus Server WMI Class

The `SMS_CM_UpdatePackDetailedSiteStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that is used to get detailed update package installation status per site.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackDetailedSiteStatus : SMS_BaseClass  
{  
    DateTime MessageTime;  
    String PackageGuid;  
    String SiteCode;  
    SInt32 SiteInstallID;  
    SInt32 SiteNumber;  
    String StatusDescription;  
    SInt32 StatusID;  
    String StatusName;  
    SInt32 SubStatusID;  
};  
```

## Methods

The `SMS_CM_UpdatePackDetailedSiteStatus` class does not define any methods.

## Properties

`MessageTime`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

The time that the message was created.

`PackageGuid`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Unique identifier of the update package.

`SiteCode`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

Unique identifier of the site.

`SiteInstallID`  
Data type: `SInt32`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

The number of installation retires.

`SiteNumber`  
Data type: `Sint32`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

Unique identifier of the site.

`StatusDescription`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Description of the status.

`StatusID`  
Data type: `Sint32`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

The status ID.

`StatusName`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the status.

`SubStatusID`  
Data type: `SInt32`

Access type: Read-only

Qualifiers: \[read, key, not\_null\]

The ID of the `SubStatus`.

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
