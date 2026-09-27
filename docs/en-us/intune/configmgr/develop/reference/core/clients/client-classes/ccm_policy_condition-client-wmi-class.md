<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_Condition Client WMI Class

In Configuration Manager, the `CCM_Policy_Condition` class is a client Windows Management Instrumentation \(WMI\) class that represents a policy condition.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Condition : CCM_Policy_Config
{
      String ConditionID;
      Boolean ConditionState;
      Object ConditionExpression;
};
```

## Properties

`ConditionID` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[key\]

Condition ID.

`ConditionState` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

Current state of the condition. This value indicates the result of the last condition evaluation, or it is `null` if the condition has never been evaluated.

`ConditionExpression` Data type: `Object`

Access type: Read-only

Qualifiers: \[read\]

Actual expression to evaluate. The value is a [CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class) object for a simple expression or a [CCM\_Policy\_Operator Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class) object for a compound expression.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class) [CCM\_Policy\_Operator Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class)
