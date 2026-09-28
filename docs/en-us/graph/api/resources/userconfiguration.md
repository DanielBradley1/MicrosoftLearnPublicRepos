<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# userConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user configuration object. User configuration objects are also known as folder associated items \(FAIs\). It's an item associated to a folder. Each user configuration object within a folder must have a unique key.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/mailsearchfolder-post-userconfigurations?view=graph-rest-beta) | [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) | Create a new [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/userconfiguration-get?view=graph-rest-beta) | [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/userconfiguration-update?view=graph-rest-beta) | [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) | Update the properties of a [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/userconfiguration-delete?view=graph-rest-beta) | None | Delete a [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| binaryData | Binary | Arbitrary binary data. |
| id | String | The unique identifier for the **userConfiguration** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| structuredData | [structuredDataEntry](https://learn.microsoft.com/en-us/graph/api/resources/structureddataentry?view=graph-rest-beta) collection | Key-value pairs of supported data types. |
| xmlData | Binary | Binary data for storing serialized XML. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userConfiguration",
  "binaryData": "String (Binary)",
  "id": "String (identifier)",
  "structuredData": [{"@odata.type": "microsoft.graph.structuredDataEntry"}],
  "xmlData": "String (Binary)"
}
```
