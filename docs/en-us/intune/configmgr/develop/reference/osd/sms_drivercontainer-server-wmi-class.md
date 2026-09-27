<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_drivercontainer-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DriverContainer Server WMI Class

The `SMS_DriverContainer` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents boot image or driver package information that refers to the specified driver.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DriverContainer : SMS_BaseClass
{
    UInt32 CI_ID;
    String Name;
    String PackageID;
    UInt32 PackageType;
};
```

## Methods

The `SMS_DriverContainer` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

The unique ID of the driver configuration item.

`Name` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Driver package or boot image name.

`PackageID` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Driver package or boot image ID.

`PackageType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
