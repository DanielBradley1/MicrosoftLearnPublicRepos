<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# teamworkUserIdentity resource type

Namespace: microsoft.graph

Represents a **user** in Microsoft Teams.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). Display name of the user. Optional. |
| id | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). ID of the user. |
| userIdentityType | teamworkUserIdentityType | Type of user. The possible values are: `aadUser`, `onPremiseAadUser`, `anonymousGuest`, `federatedUser`, `personalMicrosoftAccountUser`, `skypeUser`, `phoneUser`, `unknownFutureValue` and `emailUser`. |
| tenantId | String | Identifier of tenant, which user is part of. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkUserIdentity",
  "id": "String (identifier)",
  "displayName": "String",
  "userIdentityType": "String"
}
```
