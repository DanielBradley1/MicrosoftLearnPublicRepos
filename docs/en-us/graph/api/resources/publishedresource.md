<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-06 -->

# publishedResource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents on-premises published resource. A tenant administrator can publish various types of on-premises resources - enterprise applications, domain controllers, servers, etc. [On-premises agents](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) installed by a tenant administrator can be configured to access/handle requests to a particular published resource.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/publishedresource-list?view=graph-rest-beta) | [publishedResource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta) objects collection | Get a **publishedResources** object collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/publishedresource-get?view=graph-rest-beta) | [publishedResource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta) | Read the properties and relationships of a **publishedResource** object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/publishedresource-post?view=graph-rest-beta) | [publishedResource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta) | Create a new **publishedResource**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/publishedresource-update?view=graph-rest-beta) | [publishedResource](https://learn.microsoft.com/en-us/graph/api/resources/publishedresource?view=graph-rest-beta) | Update a **publishedResource** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/publishedresource-delete?view=graph-rest-beta) | None | Delete a **publishedResource** object. |
| [Assign to agent group](https://learn.microsoft.com/en-us/graph/api/publishedresource-post-agentgroups?view=graph-rest-beta) | None | Assign a **publishedResource** object to an **onPremisesAgentGroup**. |
| [Remove from agent group](https://learn.microsoft.com/en-us/graph/api/publishedresource-delete-agentgroups?view=graph-rest-beta) | None | Remove a **publishedResource** object from an **onPremisesAgentGroup**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display Name of the publishedResource. |
| id | String | The object id of the publishedResource. Read-only. |
| publishingType | onPremisesPublishingType | The possible values are: `applicationProxy`, `exchangeOnline`, `authentication`, `provisioning`, `intunePfx`, `oflineDomainJoin`, `unknownFutureValue`, `privateAccess`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `privateAccess`. |
| resourceName | String | Name of the publishedResource. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agentGroups | [onPremisesAgentGroup](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagentgroup?view=graph-rest-beta) collection | List of **onPremisesAgentGroups** that a **publishedResource** is assigned to. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "id": "String (identifier)",
  "publishingType": "string",
  "resourceName": "String"
}
```
