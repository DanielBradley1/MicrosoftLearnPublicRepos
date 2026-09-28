<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/endpoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Endpoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Endpoints represent URLs for resources associated with an entity. For example, when a new Microsoft 365 group is created, other resources are also created as part of the Microsoft 365 group. These include things like a group mailbox for conversations and a group OneDrive folder for documents and files. Further information about these Microsoft 365 group resources, including their associated resource URLs can now be read using the *endpoints* navigation on the group resource-type. This allows applications to understand these resources, and even embed the resource URL experiences in their own experiences.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List endpoints](https://learn.microsoft.com/en-us/graph/api/group-list-endpoints?view=graph-rest-beta) | [Endpoint](https://learn.microsoft.com/en-us/graph/api/resources/endpoint?view=graph-rest-beta) collection | Get an endpoint object collection. |
| [Get endpoint](https://learn.microsoft.com/en-us/graph/api/endpoint-get?view=graph-rest-beta) | [Endpoint](https://learn.microsoft.com/en-us/graph/api/resources/endpoint?view=graph-rest-beta) | Read properties and relationships of an endpoint object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capability | String | Describes the capability that is associated with this resource. \(for example, Messages, Conversations, etc.\) Not nullable. Read-only. |
| id | String | Unique identifier for the endpoint; Key. Not nullable. Read-only. |
| providerId | String | Application id of the publishing underlying service. Not nullable. Read-only. |
| providerName | String | Name of the publishing underlying service. Read-only. |
| providerResourceId | String | For Microsoft 365 groups, this is set to a well-known name for the resource \(for example, Yammer.FeedURL etc.\). Not nullable. Read-only. |
| uri | String | URL of the published resource. Not nullable. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "capability": "String",
  "id": "String (identifier)",
  "providerId": "String",
  "providerName": "String",
  "providerResourceId": "String",
  "uri": "String"
}
```
