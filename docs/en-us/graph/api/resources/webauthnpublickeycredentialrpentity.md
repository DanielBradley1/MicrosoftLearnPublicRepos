<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialrpentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# webauthnPublicKeyCredentialRpEntity resource type

Namespace: microsoft.graph

Represents the relying party that requests WebAuthn credential creation. The relying party is the entity, such as a website or service, that requests the creation of a credential. Configured in the **rp** proeprty of [webauthnPublicKeyCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthnpublickeycredentialcreationoptions?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The relying party identifier. For web applications, this value is typically the domain name. |
| name | String | The human-readable name for the relying party. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialRpEntity",
  "id": "String",
  "name": "String"
}
```
