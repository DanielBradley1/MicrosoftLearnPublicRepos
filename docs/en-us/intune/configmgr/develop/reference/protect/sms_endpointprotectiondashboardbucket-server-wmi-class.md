<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_endpointprotectiondashboardbucket-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_EndpointProtectionDashboardBucket Server WMI Class

The `SMS_EndpointProtectionDashboardBucket` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_EndpointProtectionDashboardBucket : SMS_BaseClass
{
    String Bucket;
    String CollectionID;
    String CollectionName;
};
```

## Methods

The `SMS_EndpointProtectionDashboardBucket` class does not define any methods.

## Properties

`Bucket` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Dashboard bucket summarized.

`CollectionID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Identifier of the collection summarized.

`CollectionName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the collection summarized.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
