<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/updateprofileidfordevices-method-in-class-sms_mdmcorpowneddevices -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateProfileIDForDevices Method in Class SMS\_MDMCorpOwnedDevices

The `UpdateProfileIdForDevices` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates the profile IDs for device serial numbers.

## Syntax

```
sint32 UpdateProfileIdForDevices(
     String RequestEnrollmentProfileId,
     String DeviceSerialNumbers
);
```

#### Parameters

`RequestEnrollmentProfileId` Data type: `String`

Qualifiers: \[in\]

Enrollment profile ID.

`DeviceSerialNumbers` Data type: `String Array`

Qualifiers: \[in\]

The serial number of the device.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_MDMCorpOwnedDevices Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_mdmcorpowneddevices-server-wmi-class)
