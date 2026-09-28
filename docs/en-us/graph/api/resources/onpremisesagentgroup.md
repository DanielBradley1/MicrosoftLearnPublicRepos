<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-06 -->

# onPremisesAgentGroup resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents on-premises agents group. Agent groups enable a tenant admin to assign specific [agents](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) to serve specific [published on-premises resources](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onpremisesagentgroup-list?view=graph-rest-beta) | onPremisesAgentGroups collection | Get an **onPremisesAgentGroup** objects collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/onpremisesagentgroup-get?view=graph-rest-beta) | [onPremisesAgentGroup](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) | Read the properties and relationships of an **onPremisesAgentGroup** object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/onpremisesagentgroup-post?view=graph-rest-beta) | [onPremisesAgentGroup](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) | Create a new **onPremisesAgentGroup**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onpremisesagentgroup-update?view=graph-rest-beta) | [onPremisesAgentGroup](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) | Update an **onPremisesAgentGroup** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/onpremisesagentgroup-delete?view=graph-rest-beta) | None | Delete an **onPremisesAgentGroup** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the **onPremisesAgentGroup**. |
| id | String | The object ID of the **onPremisesAgentGroup**. Read-only. |
| isDefault | Boolean | Indicates if the **onPremisesAgentGroup** is the default agent group. Only a single agent group can be the default **onPremisesAgentGroup** and is set by the system. |
| publishingType | onPremisesPublishingType | The possible values are: `applicationProxy`, `exchangeOnline`, `authentication`, `provisioning`, `intunePfx`, `oflineDomainJoin`, `unknownFutureValue`, `privateAccess`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `privateAccess`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agents | [onPremisesAgent](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) collection | List of **onPremisesAgent** that are assigned to an **onPremisesAgentGroup**. Read-only. Nullable. |
| publishedResources | [publishedResource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta) collection | List of **publishedResource** that are assigned to an **onPremisesAgentGroup**. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "isDefault": true,
  "publishingType": "string"
}
```
