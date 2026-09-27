<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expressionhandlerregistration-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_ExpressionHandlerRegistration Client WMI Class

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

in Configuration Manager, the `CCM_Policy_ExpressionHandlerRegistration` class is a client Windows Management Instrumentation \(WMI\) class that describes a registered expression handler for a policy. An expression handler is a COM object that implements the `ICcmPolicyExpressionHandler` interface.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_ExpressionHandlerRegistration : CCM_Policy_Config
{
      String Clsid;
      String Name;
};
```

## Methods

The `CCM_Policy_ExpressionHandlerRegistration` class does not define any methods.

## Properties

`Clsid` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

Class ID of the expression handler COM object, in registry format.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Name of the expression handler. The name is the same as the value of the `ExpressionType` property in [CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class)
