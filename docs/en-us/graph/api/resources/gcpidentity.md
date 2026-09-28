<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents GCP identities.

Inherits from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta).

The following resources inherit from this resource type:

- [gcpServiceAccount](https://learn.microsoft.com/en-us/graph/api/resources/gcpserviceaccount?view=graph-rest-beta)
- [gcpUser](https://learn.microsoft.com/en-us/graph/api/resources/gcpuser?view=graph-rest-beta)
- [gcpCloudFunction](https://learn.microsoft.com/en-us/graph/api/resources/gcpcloudfunction?view=graph-rest-beta)
- [gcpGroup](https://learn.microsoft.com/en-us/graph/api/resources/gcpgroup?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/gcpassociatedidentities-list-all?view=graph-rest-beta) | [gcpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta) collection | Get a list of the [gcpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/gcpidentity-get?view=graph-rest-beta) | [gcpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta) | Read the properties and relationships of a [gcpIdentity](https://learn.microsoft.com/en-us/graph/api/resources/gcpidentity?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the object. Supports `$filter` \(`eq`,`contains`\). Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| externalId | String | The ID for the identity as defined by GCP. Supports `$filter` \(`eq`\). Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| id | String | The ID for the identity in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| source | [authorizationSystemIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentitysource?view=graph-rest-beta) | The source of the authorization system identity. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Represents the authorization system. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpIdentity",
  "id": "String (identifier)",
  "displayName": "String",
  "source": {
    "@odata.type": "microsoft.graph.authorizationSystemIdentitySource"
  },
  "externalId": "String"
}
```
