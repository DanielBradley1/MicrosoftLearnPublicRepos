<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# servicePrincipalIdentity resource type

Namespace: microsoft.graph

Models a service principal identity.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The application identifier of the service principal. |
| displayName | String | The display name of the service principal identity. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) |
| id | String | The identifier of the service principal identity. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.servicePrincipalIdentity",
  "id": "String (identifier)",
  "displayName": "String",
  "appId": "String"
}
```
