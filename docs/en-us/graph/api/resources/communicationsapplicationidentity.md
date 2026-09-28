<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/communicationsapplicationidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# communicationsApplicationIdentity resource type

Namespace: microsoft.graph

Represents the identity of an application used for communications such as calling. You need to register the application as an enterprise application in [Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/).

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationType | String | First-party Microsoft application that presents this **identity**. |
| displayName | String | The display name associated with the application. Inherited from **identity**. |
| hidden | Boolean | `True` if the participant shouldn't be shown in other participants' rosters. |
| id | String | The client ID of the application from Microsoft Entra ID. Inherited from **identity**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "applicationType": "String",
  "displayName": "String",
  "hidden": "Boolean",
  "id": "String (identifier)"
}
```
