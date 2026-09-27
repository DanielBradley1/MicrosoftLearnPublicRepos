<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_actionhandlerregistration-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_ActionHandlerRegistration Client WMI Class

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

in Configuration Manager, the `CCM_Policy_ActionHandlerRegistration` class is a client Windows Management Instrumentation \(WMI\) class that represents an action handler registration for a policy. An action handler is a COM object that applies a particular type of policy.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_ActionHandlerRegistration : CCM_Policy_Config
{
      String Clsid;
      String Name;
      String Type;
};
```

## Methods

The `CCM_Policy_ActionHandlerRegistration` class does not define any methods.

## Properties

`Clsid` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

Class ID of the action handler COM object in registry format.

`Name` Data type`: String`

Access type: Read/Write

Qualifiers: \[key\]

Name of the action handler. This name is the same as the value of the `ActionType` property in [CCM\_Policy\_Action Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class).

`Type` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

The type of the action handler, which defaults to WMI. The handler implements the `ICcmPolicyWmiActionHandler` interface for creating WMI objects in the `RequestConfig` namespace.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_Policy\_Action Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class)
