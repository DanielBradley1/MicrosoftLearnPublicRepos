<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privilegeescalationfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# privilegeEscalationFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents findings for a list of potential exploiting of a misconfigured IAM policy or configuration oversight to gain elevated access to other permissions and resources in AWS and GCP.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| identityDetails | [identityDetails](https://learn.microsoft.com/en-us/graph/api/resources/identitydetails?view=graph-rest-beta) | An identity's information details. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| permissionsCreepIndex | [permissionsCreepIndex](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta) | \*A score for an identity's excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high. This property and its values are a snapshot as of when the finding was created and might not reflect the current score for the identity. Supports `$filter` \(`gt`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identity | [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) | Represents an identity in an authorization system onboarded to Permissions Management. Inherited from [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta). Autoexpanded by default. |
| privilegeEscalationDetails | [privilegeEscalation](https://learn.microsoft.com/en-us/graph/api/resources/privilegeescalation?view=graph-rest-beta) collection | The list of escalations that the identity is capable of performing. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privilegeEscalationFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "permissionsCreepIndex": {
    "@odata.type": "microsoft.graph.permissionsCreepIndex"
  },
  "identityDetails": {
    "@odata.type": "#microsoft.graph.identityDetails"
  }
}
```
