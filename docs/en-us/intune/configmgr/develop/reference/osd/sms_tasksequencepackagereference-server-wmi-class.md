<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackagereference-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequencePackageReference Server WMI Class

The `SMS_TaskSequencePackageReference` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a Configuration Manager application or package in the task sequence.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequencePackageReference : SMS_BaseClass
{
    String Description;
    String ObjectID;
    String ObjectName;
    UInt32 ObjectType;
    String PackageID;
    String Version;
};
```

## Methods

The `SMS_TaskSequencePackageReference` class does not define any methods.

## Properties

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reference object description.

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Reference object ID.

`ObjectName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reference object name.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

Reference object type.

| Value | Object type |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 5 | PKG\_TYPE\_SWUPDATES |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Task sequence package ID.

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reference object version.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
