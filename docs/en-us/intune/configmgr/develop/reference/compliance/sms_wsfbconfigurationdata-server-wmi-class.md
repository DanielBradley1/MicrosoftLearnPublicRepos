<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_wsfbconfigurationdata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_WSfBConfigurationData Server WMI Class

The `SMS_WSfBConfigurationData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft Store for Business configuration data.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_WSfBConfigurationData : SMS_BaseClass
{
    String ClientId;
    String ContentLocation;
    String DefaultLocale;
    DateTime LastSuccessfulSyncTime;
    SInt32 LastSyncStatus;
    DateTime LastSyncTime;
    String SelectedLocales;
    String TenantId;
};
```

## Methods

The `SMS_WSfBConfigurationData` class does not define any methods.

## Properties

`ClientId` Data type: `String`

Access type: Read

Qualifiers: none

Microsoft Store For Business client ID.

`ContentLocation` Data type: `String`

Access type: Read

Qualifiers: none

Location of the content downloaded from the Microsoft Store For Business.

`DefaultLocale` Data type: `String`

Access type: Read

Qualifiers: none

The default language for the Microsoft Store for Business.

`LastSuccessfulSyncTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The time of the last successful synchronization with Microsoft Store for Business.

`LastSyncStatus` Data type: `SInt32`

Access type: Read

Qualifiers: none

The status of the last synchronization with Microsoft Store for Business.

`LastSyncTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The time of the last synchronization with Microsoft Store for Business.

`SelectedLocales` Data type: `String`

Access type: Read

Qualifiers: none

The selected languages for Microsoft Store for Business.

`TenantId` Data type: `String`

Access type: Read

Qualifiers: \[key\]

Microsoft Store for Business tenant ID.

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

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes)
