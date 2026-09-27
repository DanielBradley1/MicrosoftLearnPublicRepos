<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_advancedthreatprotectionhealthstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System\_AdvancedThreatProtectionHealthStatus Server WMI Class

The `SMS_G_System_AdvancedThreatProtectionHealthStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Microsoft Defender for Endpoint client health status.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_AdvancedThreatProtectionHealthStatus : SMS_G_System
{
    DateTime LastConnected;
    UInt32 OnboardingState;
    String OrgId;
    UInt32 ResourceID;
    Boolean SenseIsRunning;
};
```

## Methods

The `SMS_G_System_AdvancedThreatProtectionHealthStatus` class does not define any methods.

## Properties

`LastConnected` Data type: `DateTime`

Access type: Read

Qualifiers: \[not\_null\]

The time that the Microsoft Defender for Endpoint agent last connected to the cloud.

`OnboardingState` Data type: `UInt32`

Access type: Read

Qualifiers: \[not\_null\]

The onboarding state.

`OrgId` Data type: `String`

Access type: Read

Qualifiers: \[not\_null\]

The ID of the organization that the Microsoft Defender for Endpoint agent reports to.

`ResourceID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key, not\_null\]

See [SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class).

`SenseIsRunning` Data type: `Boolean`

Access type: Read

Qualifiers: \[not\_null\]

Indicates whether the Microsoft Defender for Endpoint agent is running.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
