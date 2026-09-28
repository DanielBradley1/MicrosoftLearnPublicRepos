<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionauthorizationsystemidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsDefinitionAuthorizationSystemIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an identity that's requesting permissions in an authorization system, either directly or indirectly.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalId | String | Unique ID of the identity within the external system. Prefixed with `rsn:` if this is a SAML or ED user in AWS. Alternate key. |
| identityType | permissionsDefinitionIdentityType | The type of identity that is assigned the permission in the authorization system. The possible values are: `user`, `role`, `application`, `managedIdentity`, `serviceAccount`, `unknownFutureValue`. |
| source | [permissionsDefinitionIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/permissionsdefinitionidentitysource?view=graph-rest-beta) | The source system for the identity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsDefinitionAuthorizationSystemIdentity",
  "externalId": "String (identifier)",
  "identityType": "String",
  "source": {
    "@odata.type": "microsoft.graph.permissionsDefinitionIdentitySource"
  }
}
```
