<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_windowsservicinglocalizednames-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_WindowsServicingLocalizedNames Server WMI Class

For internal use only.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_WindowsServicingLocalizedNames : SMS_BaseClass
{
    UInt32 LocaleID;
    String Name;
    String Value;
};
```

## Methods

The `SMS_WindowsServicingLocalizedNames` class does not define any methods.

## Properties

`LocaleID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key, not\_null\]

Reserved for internal use.

`Name` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null\]

Reserved for internal use.

`Value` Data type: `String`

Access type: Read

Qualifiers: none

Reserved for internal use.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
