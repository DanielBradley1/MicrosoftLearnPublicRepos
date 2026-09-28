<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# filteringPolicyLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The association between a policy and a [filtering profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta). This resource is an abstract type for associating the following derived policies with a filtering profile:

- [microsoft.graph.networkaccess.cloudFirewallPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicylink?view=graph-rest-beta)
- [microsoft.graph.networkaccess.threatIntelligencePolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicylink?view=graph-rest-beta)
- [microsoft.graph.networkaccess.tlsInspectionPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicylink?view=graph-rest-beta)

Inherits from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-list?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-post?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) | Create a [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) object and its properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) | Get a [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.networkaccess.filteringPolicyAction | The actions for filtering policies, offering "block" and "allow" options to specify whether to block or allow access based on the policy. The possible values are: `block`, `allow`. |
| createdDateTime | DateTimeOffset | The date and time when the filtering Policy link was created. |
| id | String | Unique identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was most recently modified. |
| loggingState | microsoft.graph.networkaccess.status | A value that tells whether the link is enabled or disabled. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). The allowed values are `enabled` and `disabled`. |
| priority | Int64 | Provides an integer priority level for each instance of a URL filtering policy linked to a profile. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) | The definition of the policy ruleset that makes up the core definition of a policy. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). Automatically expanded. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.filteringPolicyLink",
  "id": "String (identifier)",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "priority": "Integer",
  "action": "String",
  "loggingState": "String"
}
```
