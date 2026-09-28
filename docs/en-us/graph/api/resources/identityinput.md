<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityinput?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-23 -->

# identityInput resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a person, group, or other recipient used as input to resolve identities during creation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alias | String | The alias of the identity. |
| email | String | The email of the identity. |
| objectId | String | The unique object ID assigned to the identity in Microsoft Entra ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityInput",
  "alias": "String",
  "email": "String",
  "objectId": "String"
}
```
