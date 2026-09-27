<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_rule-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_Rule Client WMI Class

In Configuration Manager, the `CCM_Policy_Rule` class is a client Windows Management Instrumentation \(WMI\) class that defines a policy object rule. Objects of this class are only used in the `PolicyRules` property in [CCM\_Policy\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_policy-client-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class  CCM_Policy_Rule : CCM_Policy_Config
{
      String RuleID;
      String RuleCondition;
      Object RuleActions[];
};
```

## Properties

`RuleID` Data type: `String`

Access type: Read-only

Qualifiers: \[key\]

Unique ID of the rule within the policy object.

`RuleCondition` Data type: `String`

Access type: Read-only

Qualifiers: None

Optional. Rule condition. If the condition is not NULL, set this property to the unique ID of a [CCM\_Policy\_Condition Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class) object. The rule is only applied if the policy is active and the rule condition evaluates to TRUE.

`RuleActions` Data type: `Object` Array

Access type: Read-only

Qualifiers: None

Array of [CCM\_Policy\_Action Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class) objects specifying the actions to perform when the rule is applied.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_Policy\_Condition Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class) [CCM\_Policy\_Action Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_action-client-wmi-class)
