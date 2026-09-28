<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# microsoftStoreForBusinessContainedApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class that represents a contained app of a MicrosoftStoreForBusinessApp.

Inherits from [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftStoreForBusinessContainedApps](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinesscontainedapp-list?view=graph-rest-beta) | [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) collection | List properties and relationships of the [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) objects. |
| [Get microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinesscontainedapp-get?view=graph-rest-beta) | [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) | Read properties and relationships of the [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) object. |
| [Create microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinesscontainedapp-create?view=graph-rest-beta) | [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) | Create a new [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) object. |
| [Delete microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinesscontainedapp-delete?view=graph-rest-beta) | None | Deletes a [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta). |
| [Update microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/intune-apps-microsoftstoreforbusinesscontainedapp-update?view=graph-rest-beta) | [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) | Update the properties of a [microsoftStoreForBusinessContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-microsoftstoreforbusinesscontainedapp?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [mobileContainedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobilecontainedapp?view=graph-rest-beta) |
| appUserModelId | String | The app user model ID of the contained app of a MicrosoftStoreForBusinessApp. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftStoreForBusinessContainedApp",
  "id": "String (identifier)",
  "appUserModelId": "String"
}
```
