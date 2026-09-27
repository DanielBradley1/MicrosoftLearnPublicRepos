<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_bitsconfiguration-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Service\_BITSConfiguration Client WMI Class

In Configuration Manager, the `CCM_Service_BITSConfiguration` class is a client Windows Management Instrumentation \(WMI\) class that supports Background Intelligent Transfer Service \(BITS\)-related settings used by CCMEXEC for uploading and downloading message payloads. The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_BITSConfiguration : CCM_Policy
{
      UInt8 DummyKey;
      UInt32 MinimumRetryDelay;
      UInt32 NoProgressTimeout;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Service_BITSConfiguration` class does not define any methods.

## Properties

`DummyKey` Data type: `UInt8`

Access type: Read/Write

Qualifiers: None

This value is used as the WMI key for a singleton policy and has no other effect.

`MinimumRetryDelay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Retry delay to pass to BITS when uploading or downloading message payloads \(in minutes\). If the value is 0 or `null`, BITS defaults are used.

`NoProgressTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

No-progress timeout to pass to BITS when uploading or downloading message payloads \(in minutes\). If the value is `null` or 0, BITS defaults are used.

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: Key

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Client Framework and Data Transfer Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/client-framework-and-data-transfer-client-wmi-classes) [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class)
