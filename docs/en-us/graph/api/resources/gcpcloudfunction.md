<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcpcloudfunction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpCloudFunction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a cloud function in a GCP authorization system.

Inherits from [gcpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the object. Supports `$filter` and \(`eq`\). Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| externalId | String | The ID for the cloud function as defined by GCP. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| id | String | The ID for the cloud function in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| source | [authorizationSystemIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentitysource?view=graph-rest-beta) | The source of the authorization system identity. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Represents the authorization system. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) |
| resource | [awsAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta) | Represents the resources in an authorization system.. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpCloudFunction",
  "id": "String (identifier)",
  "displayName": "String",
  "source": {
    "@odata.type": "microsoft.graph.authorizationSystemIdentitySource"
  },
  "externalId": "String"
}
```
