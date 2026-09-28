<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialuserentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnPublicKeyCredentialUserEntity resource type

Namespace: microsoft.graph

Represents information about the user account for which a credential is being created. This information is used by the authenticator to associate the credential with the user. This complex type is the type for the **user** property of the [webauthnPublicKeyCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | A human-readable name for the user account, intended for display. |
| id | String | A user identifier, determined by the relying party. This value is opaque to the authenticator and is Base64URL-encoded without padding. |
| name | String | A human-readable identifier for the user account, such as a username or email address. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialUserEntity",
  "id": "String",
  "displayName": "String",
  "name": "String"
}
```
