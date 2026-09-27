<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_dirfullcollmem-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_DirFullCollMem Server WMI Class

The `SMS_DirFullCollMem` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the full collection membership of directly assigned collections.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DirFullCollMem : SMS_BaseClass
{
    String CollectionID;
    UInt32 ResourceID;
};
```

## Methods

The `SMS_DirFullCollMem` class doesn't define any methods.

## Properties

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Unique auto-generated ID containing eight characters that identifies a collection.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Unique Configuration Manager-supplied ID for the resource.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
