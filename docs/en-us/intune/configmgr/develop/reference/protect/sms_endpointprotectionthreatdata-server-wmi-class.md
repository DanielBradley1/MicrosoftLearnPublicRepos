<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/protect/sms_endpointprotectionthreatdata-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SMS\_EndpointProtectionThreatData Server WMI Class

The `SMS_EndpointProtectionThreatData` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft official threats. This is a metadata table/view and all data is extracted from the signature update.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_EndpointProtectionThreatData : SMS_BaseClass
{
    UInt32 DefaultActionID;
    UInt32 IsAV;
    String Name;
    UInt64 ThreatID;
    UInt32 VersionFirstUpdated;
};
```

## Methods

The `SMS_EndpointProtectionThreatData` class doesn't define any methods.

## Properties

`DefaultActionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier of the action the EndPoint Protection agent takes for this particular threat.

| Value | Default action |
| --- | --- |
| 0 | Recommend |
| 2 | Quarantine |
| 3 | Remove |
| 6 | Allow |

`IsAV` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Is Antimalware or Antispyware.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

Threat name.

`ThreatID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: \[key\]

Threat identifier.

`VersionFirstUpdated` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Signature version.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
