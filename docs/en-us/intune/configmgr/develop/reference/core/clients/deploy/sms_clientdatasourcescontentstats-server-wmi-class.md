<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdatasourcescontentstats-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ClientDataSourcesContentStats Server WMI Class

The `SMS_ClientDataSourcesContentStats` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents client content data sources per package.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientDataSourcesContentStats : SMS_BaseClass
{
    UInt64 BytesDownloaded;
    String ContentName;
    UInt32 SourceType;
};
```

## Methods

The `SMS_ClientDataSourcesContentStats` class does not define any methods.

## Properties

`BytesDownloaded` Data type: `UInt64`

Access type: Read

Qualifiers: none

Number of bytes downloaded.

`ContentName` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null\]

The name of the content.

`SourceType` Data type: `UInt32`

Access type: Read

Qualifiers: \[key, not\_null\]

Source type.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
