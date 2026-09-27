<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_operator-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_Operator Client WMI Class

In Configuration Manager, the `CCM_Policy_Operator` class is a client Windows Management Instrumentation \(WMI\) class that stores a compound expression that evaluates to either `true` or `false`.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
class CCM_Policy_Operator : CCM_Policy_Config
{
      String OperatorType;
   Object Operands[];
};
```

## Properties

`OperatorType` Data type: `String`

Access type: Read-only

Qualifier: \[Not\_Null:ToInstance\]

The type of operator. Possible values are:

| Value | Description |
| --- | --- |
| `AND` | A logical `AND` operator. The result of the compound expression is only `true` if all of its operands evaluate to `true`. |
| `OR` | A logical `OR` operator. The result of the compound expression is `true` if any one of its operands evaluates to `true`. |
| `NOT` | A logical `NOT` operator. This operator can only have a single operand. The result of the expression is `true` only if the operand evaluates to `false`. |

`Operands` Data type: `Object`

Access type: Read-only

Qualifier: \[Not\_Null:ToInstance\]

Operands for the compound expression. Each operand can be a [CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class) object or a `CCM_Policy_Operator` object if further nesting is required.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_Policy\_Expression Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_expression-client-wmi-class)
