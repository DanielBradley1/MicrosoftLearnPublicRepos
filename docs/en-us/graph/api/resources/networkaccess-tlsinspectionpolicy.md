<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionPolicy resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Let's you configure TLS termination for your organization's network traffic within Global Secure Access. You can link the policy to a filtering profile using the [microsoft.graph.networkaccess.tlsInspectionPolicyLink resource](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicylink?view=graph-rest-beta). Each filtering profile can hold only one **tlsInspectionPolicyLink**.

Inherits from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List policies](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-tlsinspectionpolicies?view=graph-rest-beta) | [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) collection | Get a list of tlsInspectionPolicy objects. |
| [Get policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-get?view=graph-rest-beta) | [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) | Get a single tlsInspectionPolicy object. |
| [Create policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-post-tlsinspectionpolicies?view=graph-rest-beta) | [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) | Create a new tlsInspectionPolicy. |
| [Update policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-update?view=graph-rest-beta) | None | Update properties of a tlsInspectionPolicy object. |
| [Delete policy](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-delete?view=graph-rest-beta) | None | Delete a tlsInspectionPolicy object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Optional description of the policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`, `startsWith`\) |
| id | String | The unique identifier for the policy. Read-only. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The timestamp of when the policy was last modified. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\) and `$orderby`. Read-only. |
| name | String | The display name of the policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| settings | [microsoft.graph.networkaccess.tlsInspectionPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicysettings?view=graph-rest-beta) | Settings that configure the default behavior of the policy. |
| version | String | Version number of the policy. Supports `$filter` \(`eq`, `ne`, `startsWith`\). Read-only. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policyRules | [microsoft.graph.networkaccess.tlsInspectionRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) collection | Collection of rules that define the specific matching conditions and desired actions for TLS inspection. Must contain rules of type `tlsInspectionRule` only. Inherited from Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |

## JSON representation

The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "settings": {
    "@odata.type": "microsoft.graph.networkaccess.tlsInspectionPolicySettings"
  },
  "version": "String"
}
```
