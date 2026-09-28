<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/uxsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-06 -->

# uxSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings related to access to the Microsoft Entra admin center.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/uxsetting-get?view=graph-rest-beta) | [uxSetting](https://learn.microsoft.com/en-us/graph/api/resources/uxsetting?view=graph-rest-beta) | Get the properties and relationships of a [uxSetting](https://learn.microsoft.com/en-us/graph/api/resources/uxsetting?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/uxsetting-update?view=graph-rest-beta) | None | Update the properties of a [uxSetting](https://learn.microsoft.com/en-us/graph/api/resources/uxsetting?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the tenant. |
| restrictNonAdminAccess | nonAdminSetting | If set to `true`, nonadministrators can't browse the Microsoft Entra admin center. Nonadministrators who are owners of groups or applications are unable to use the Azure portal to manage their owned resources. If set to `false`, nonadministrators can browse the Microsoft Entra admin center. The possible values are: `false`, `true`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.uxSetting",
  "id": "String (identifier)",
  "restrictNonAdminAccess": "String"
}
```
