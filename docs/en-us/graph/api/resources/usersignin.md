<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usersignin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# userSignIn resource type

Namespace: microsoft.graph

Defines details of the user that is signing in, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). Inherits from [signInIdentity](https://learn.microsoft.com/en-us/graph/api/resources/signinidentity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalTenantId | String | TenantId of the guest user as applies to Microsoft Entra B2B scenarios. |
| externalUserType | conditionalAccessGuestOrExternalUserTypes | Category that the guest user belongs to. The possible values are: `none`, `internalGuest`, `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `otherExternalUser`, `serviceProvider`, `unknownFutureValue`. |
| userId | String | Object ID of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userSignIn",
  "userId": "String",
  "externalUserType": "String",
  "externalTenantId": "String"
}
```
