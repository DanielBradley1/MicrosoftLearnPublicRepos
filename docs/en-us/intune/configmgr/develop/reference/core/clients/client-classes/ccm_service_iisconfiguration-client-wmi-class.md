<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_iisconfiguration-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Service\_IISConfiguration Client WMI Class

In Configuration Manager, the `CCM_Service_IISConfiguration` class is a client Windows Management Instrumentation \(WMI\) class that supports Internet Information Services \(IIS\)-related settings used by CCMEXEC for staging and receiving message payloads on a Management Point.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_IISConfiguration : CCM_Policy
{
      UInt8 Dummy[key]  ;
      String IncomingPayloadDir;
      String IncomingPayloadVirtualDir;
      String OutgoingPayloadDir;
      String OutgoingPayloadVirtualDir;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
};
```

## Methods

The `CCM_Service_IISConfiguration` class does not define any methods.

## Properties

`Dummy[key]` Data type: `UInt8`

Access type: Read/Write

Qualifiers: \[Realkey\]

Dummy key.

`IncomingPayloadDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Directory where message payloads are uploaded to the server by clients. The System and Administrators account must have full access to this directory. In addition, the appropriate permissions must be given to allow clients to upload to this directory by means of IIS using the BITS ISAPI component. This directory must be created at install time; it is not automatically created by the service.

`IncomingPayloadVirtualDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

IIS virtual directory mapped to **IncomingPayloadDir**.

`OutgoingPayloadDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Directory that is used to hold message payloads that will be downloaded by clients.

`OutgoingPayloadVirtualDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

IIS virtual directory mapped to **OutgoingPayloadDir**.

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

## Remarks

An instance of this class should exist only if IIS has been configured to work with CCMEXEC, that is, IIS must be installed and the appropriate physical and virtual directories must be set up correctly. If this instance is omitted, CCMEXEC operates without using IIS, thus losing some functionality.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Client Framework and Data Transfer Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/client-framework-and-data-transfer-client-wmi-classes)
