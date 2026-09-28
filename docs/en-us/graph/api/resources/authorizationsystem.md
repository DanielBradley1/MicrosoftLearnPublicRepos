<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# authorizationSystem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a Microsoft Azure susbcription, Amazon Web Services \(AWS\) account, or Google Cloud Platform \(GCP\) project onboarded onto Microsoft Entra Permissions Management, Microsoft's cloud infrastructure entitlement management \(CIEM\) solution. Permissions Management discovers, remediates, and monitors the permissions and actions of identities in these platforms.

This object is read-only and is populated when you successfully onboard the platform onto Permissions Management.

The following resource types are derived from this resource:

- [awsAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystem?view=graph-rest-beta) resource type
- [azureAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystem?view=graph-rest-beta) resource type
- [gcpAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystem?view=graph-rest-beta) resource type

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/externalconnectors-external-list-authorizationsystems?view=graph-rest-beta) | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) collection | Get a list of the [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/authorizationsystem-get?view=graph-rest-beta) | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Read the properties and relationships of an [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizationSystemId | String | ID of the authorization system retrieved from the customer cloud environment. Supports `$filter`\(`eq`, `contains`\) and `$orderBy`. |
| authorizationSystemName | String | Name of the authorization system detected after onboarding. Supports `$filter`\(`eq`,`contains`\) and `$orderBy`. |
| authorizationSystemType | String | The type of authorization system. Can be `gcp`, `azure`, or `aws`. Supports `$filter`\(`eq`\). |
| id | String | Unique identifier for the authorization system within Microsoft Entra Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| dataCollectionInfo | [dataCollectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/datacollectioninfo?view=graph-rest-beta) | Defines how and whether Permissions Management collects data from the onboarded authorization system. Supports `$filter` \(`eq`\) as follows: `$filter=dataCollectionInfo/entitlements/permissionsModificationCapability` and `$filter=dataCollectionInfo/entitlements/status`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationSystem",
  "id": "String (identifier)",
  "authorizationSystemId": "String",
  "authorizationSystemName": "String",
  "authorizationSystemType": "String"
}
```
