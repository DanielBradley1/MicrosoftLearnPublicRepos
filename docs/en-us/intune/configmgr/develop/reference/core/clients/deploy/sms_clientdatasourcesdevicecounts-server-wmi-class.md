<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdatasourcesdevicecounts-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ClientDataSourcesDeviceCounts Server WMI Class

The `SMS_ClientDataSourcesContentStats` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents device counts for client data sources.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientDataSourcesDeviceCounts : SMS_BaseClass
{
    UInt32 ClientCount;
    UInt32 DPCount;
    UInt32 PeerClientCount;
};
```

## Methods

The `SMS_ClientDataSourcesDeviceCounts` class does not define any methods.

## Properties

`ClientCount` Data type: `UInt32`

Access type: Read

Qualifiers: none

The number of clients.

`DPCount` Data type: `UInt32`

Access type: Read

Qualifiers: none

The number of distribution points.

`PeerClientCount` Data type: `UInt32`

Access type: Read

Qualifiers: none

The number of peer clients.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)
- Singleton
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
