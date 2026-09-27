<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_drivermodel-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DriverModel Server WMI Class

The `SMS_DriverModel` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents driver model information for the specified driver.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DriverModel : SMS_BaseClass
{
    UInt32 CI_ID;
    String CI_UniqueID;
    String ModelManufacture;
    String ModelName;
};
```

## Methods

The `SMS_DriverModel` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Driver configuration item local unique ID.

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Driver configuration item global unique ID.

`ModelManufacture` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Driver configuration item Model manufacturer.

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, not\_null, read\]

Driver configuration item Model name.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
