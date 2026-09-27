<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupcollections-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DPGroupCollections Server WMI Class

The `SMS_DPGroupCollections` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that describes collection association for a given distribution point group.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupCollections : SMS_BaseClass
{
    String CollectionDescription;
    String CollectionID;
    UInt32 CollectionMemberCount;
    String CollectionName;
    String GroupDescription;
    String GroupID;
    String GroupName;
};
```

## Methods

The `SMS_DPGroupCollections` class does not define any methods.

## Properties

`CollectionDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the collection.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Collection associated with the distribution point group.

`CollectionMemberCount` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Count of the collection members.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection.

`GroupDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the distribution point group.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Identifier for the distribution point group.

`GroupName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the distribution point group.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
