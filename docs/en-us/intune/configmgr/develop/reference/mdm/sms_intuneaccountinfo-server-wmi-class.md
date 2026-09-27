<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_intuneaccountinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_IntuneAccountInfo Server WMI Class

The `SMS_IntuneAccountInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft Intune account information.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_IntuneAccountInfo : SMS_BaseClass
{
    String AADTenantID;
    String IntuneAccountID;
    Datetime LastUpdateTime;
};
```

## Methods

The `SMS_IntuneAccountInfo` class does not define any methods.

## Properties

`AADTenantID` Data type: `String`

Access type: Read

Qualifiers: none

The GUID of the Microsoft Entra account.

`IntuneAccountID` Data type: `String`

Access type: Read

Qualifiers: \[key\]

The GUID of the Microsoft Intune account.

`LastUpdateTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The last date and time that the account was updated.

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
