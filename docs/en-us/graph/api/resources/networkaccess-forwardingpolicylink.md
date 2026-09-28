<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# forwardingPolicyLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A forwardingPolicyLink represents the association between a [forwarding policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicy?view=graph-rest-beta) and a [forwarding profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingprofile?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingprofile-list-policies?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingpolicylink-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingpolicylink-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-forwardingpolicylink-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.networkaccess.forwardingPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-forwardingpolicylink?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | microsoft.graph.networkaccess.status | Link Status. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). The possible values are: `enabled`, `disabled`. |
| version | String | Version number. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). |
| priority | Int32 | Priority of the policy within the forwarding profile. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) | A traffic forwarding policy consists of a policy and its associated rules. It defines the guidelines and instructions for routing and handling network traffic.. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.forwardingPolicyLink",
  "id": "String (identifier)",
  "state": "String",
  "version": "String",
  "priority": "Integer"
}
```
