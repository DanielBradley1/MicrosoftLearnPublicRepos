<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncservice-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ActiveSyncService Client WMI Class

The `SMS_ActiveSyncService` class is a client Windows Management Instrumentation \(WMI\) class, in Configuration Manager, that represents the ActiveSync service on the client.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ActiveSyncService : SMS_Class_Template
{
      String LastSyncTime;
      UInt32 MajorVersion;
      UInt32 MinorVersion;
};
```

## Methods

The `SMS_ActiveSyncService` class does not define any methods.

## Properties

`LastSyncTime` Data type: `String`

Access type: Read/Write

Qualifiers:

\[SMS\_Report\("True"\)\]

The last time when the client was synchronized with connected devices.

`MajorVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[SMS\_Report\("True"\), key\]

The major version number of the client operating system.

`MinorVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[SMS\_Report\("True"\), key\]

The minor version number of the client operating system.

## Remarks

All properties of this class are marked with qualifiers to indicate that they represent items that are generated dynamically \(reported\) based on the content of the SMS\_def.mof file.

## See Also

[Device Management Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/device-management-client-wmi-classes) [SMS\_ActiveSyncConnectedDevice Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_activesyncconnecteddevice-client-wmi-class)
