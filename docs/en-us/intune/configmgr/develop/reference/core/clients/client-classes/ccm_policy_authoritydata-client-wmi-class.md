<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy_authoritydata-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Policy\_AuthorityData Client WMI Class

In Configuration Manager, the `CCM_Policy_AuthorityData` class is a client Windows Management Instrumentation \(WMI\) class that stores information about policy from a particular authority.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Policy_AuthorityData : CCM_Policy_Config
{
      DateTime LastReplyTime;
      String Name;
      String ServerCookie;
};
```

## Methods

The `CCM_Policy_AuthorityData` class does not define any methods.

## Properties

`LastReplyTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The last date and time when the authority replied to a request for policy assignments. If this value is older than the value of `PolicyTimeUntilAck` in the authority's [CCM\_PolicyAgent\_Configuration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class) object, the policy requests an acknowledgment. If the value is older than the value of `PolicyTimeUntilExpire`, the policy is expired.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Name of the authority to which the data applies.

`ServerCookie` Data type: `String`

Access type: Read/Write

Qualifiers: None

The last `ServerCookie` value received from the authority in a `ReplyAssignments` message.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Policy Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/policy-agent-client-wmi-classes) [CCM\_PolicyAgent\_Configuration Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policyagent_configuration-client-wmi-class)
