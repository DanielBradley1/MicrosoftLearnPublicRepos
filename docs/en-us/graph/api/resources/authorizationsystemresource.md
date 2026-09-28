<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# authorizationSystemResource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a resource in an authorization system onboarded to Permissions Management. The following resource types are derived from this base type: awsAuthorizationSystemResource, azureAuthorizationSystemResource, and gcpAuthorizationSystemResource.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the resource. Read-only. Supports `$filter` \(`eq`,`contains`\). |
| externalId | String | The ID of the resource as defined by the authorization system provider. Read-only. Supports `$filter` \(`eq`\). |
| id | String | The ID for the resource as defined by Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Read-only. |
| resourceType | String | The type of the resource. Read-only. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | The authorization system that the resource exists in. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationSystemResource",
  "id": "String (identifier)",
  "externalId": "String",
  "displayName": "String",
  "resourceType": "String"
}
```
