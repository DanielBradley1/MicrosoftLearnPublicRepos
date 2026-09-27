<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionbucket-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionBucket Server WMI Class

The `SMS_CollectionBucket` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents joining of collection and bucket. By default, all collections will have a client health related bucket, while the endpoint protection bucket is only applicable to endpoint protection allowed collections.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionBucket : SMS_BaseClass
{
    String Bucket;
    String CollectionID;
    String CollectionName;
    UInt32 FeatureType;
};
```

## Methods

The `SMS_CollectionBucket` class does not define any methods.

## Properties

`Bucket` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Bucket summarized.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Identifier of collection summarized.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of collection summarized.

`FeatureType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Identifier of feature type.

| Value | Feature Type |
| --- | --- |
| 1 | EndPoint Protection |
| 2 | Client Check |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
