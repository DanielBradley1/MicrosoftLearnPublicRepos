<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/photoupdatesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# photoUpdateSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings that manage the support of photos modified in an organization. By default, photo updates are disabled. If enabled, users can optionally add or update their photo update settings.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-photoupdatesettings?view=graph-rest-beta) | [photoUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/photoupdatesettings?view=graph-rest-beta) | Get the properties of a [photoUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/photoupdatesettings?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/photoupdatesettings-update?view=graph-rest-beta) | [photoUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/photoupdatesettings?view=graph-rest-beta) | Update the properties of a [photoUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/photoupdatesettings?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for a peopleAdminSettings object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| source | String | Specifies the types of photo updates permitted. The possible values are: `cloud`, `onPremises`, `unknownFutureValue`. |
| allowedRoles | String collection | Contains a list of roles to perform edit operations in the cloud. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.photoUpdateSettings",
  "id": "String (identifier)",
  "source": "String",
  "allowedRoles": [
    "String"
  ]
}
```
