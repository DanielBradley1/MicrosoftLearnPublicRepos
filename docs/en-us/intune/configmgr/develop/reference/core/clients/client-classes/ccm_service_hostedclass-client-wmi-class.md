<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_hostedclass-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Service\_HostedClass Client WMI Class

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

in Configuration Manager, the `CCM_Service_HostedClass` class is a client Windows Management Instrumentation \(WMI\) class that configures a COM class to be hosted in the CCMEXEC service.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_HostedClass : CCM_Policy
{
      String CLSID;
      String Description;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Service_HostedClass` class does not define any methods.

## Properties

`CLSID` Data type: `String`

Access type: Read/Write

Qualifiers: \[Realkey\]

CLSID of the COM class that will be hosted in the service. The class must be registered as an in-process DLL component and be associated with the same application ID as CCMEXEC.

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

COM class description.

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

Qualifiers: \[key\]

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

[Client Framework and Data Transfer Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/client-framework-and-data-transfer-client-wmi-classes)
