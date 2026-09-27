<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_assignment-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_Assignment Client WMI Class

In Configuration Manager, the `CCM_Policy_Assignment` class is a client Windows Management Instrumentation \(WMI\) class that represents a policy assignment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_Assignment : CCM_Policy_Config
{
      String AssignmentCondition;
      String AssignmentCookie;
      String AssignmentID;
      ref:CCM_Policy_Policy AssignmentPolicy;
      String AssignmentSource;
};
```

## Methods

The `CCM_Policy_Assignment` class does not define any methods.

## Properties

`AssignmentCondition` Data type: `String`

Access type: Read/Write

Qualifiers: None

Assignment condition that determines if the policy should be applied to the assignment. Set this property to NULL if the policy always applies, or to the ID of a particular policy condition, represented by [CCM\_Policy\_Condition Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class).

`AssignmentCookie` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null:ToInstance\]

Arbitrary data used by the source authority.

`AssignmentID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Unique ID of the assignment.

`AssignmentPolicy` Data type: `ref:CCM_Policy_Policy`

Access type: Read-only

Qualifiers: \[read, Not\_Null:ToInstance\]

Reference to the policy object to which the assignment applies.

`AssignmentSource` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, Not\_Null:ToInstance\]

Source authority of the assignment.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_Policy\_Condition Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_condition-client-wmi-class)
