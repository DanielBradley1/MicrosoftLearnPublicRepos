<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# learningProvider resource type

Namespace: microsoft.graph

Represents an entity that holds the details about a learning provider in Viva learning.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-learningproviders?view=graph-rest-1.0) | [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) collection | Get a list of the [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) resources registered in Viva Learning for a tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/employeeexperience-post-learningproviders?view=graph-rest-1.0) | [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) | Create a new [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) object and register it with Viva Learning using the specified display name and logos for different themes. |
| [Get](https://learn.microsoft.com/en-us/graph/api/learningprovider-get?view=graph-rest-1.0) | [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) | Read the properties and relationships of a [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/learningprovider-update?view=graph-rest-1.0) | [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) | Update the properties of a [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/employeeexperience-delete-learningproviders?view=graph-rest-1.0) | None | Delete a [learningProvider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) resource and remove its registration in Viva Learning for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name that appears in Viva Learning. Required. |
| id | String | The unique identifier for the learning provider. Required. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isCourseActivitySyncEnabled | Boolean | Indicates whether a provider can ingest learning course activity records. The default value is `false`. Set to `true` to make learningCourseActivities available for this provider. |
| loginWebUrl | String | Authentication URL to access the courses for the provider. Optional. |
| longLogoWebUrlForDarkTheme | String | The long logo URL for the dark mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |
| longLogoWebUrlForLightTheme | String | The long logo URL for the light mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |
| squareLogoWebUrlForDarkTheme | String | The square logo URL for the dark mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |
| squareLogoWebUrlForLightTheme | String | The square logo URL for the light mode that needs to be a publicly accessible image. This image would be saved to the blob storage of Viva Learning for rendering within the Viva Learning app. Required. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| learningContents | [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) collection | Learning catalog items for the provider. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.learningProvider",
  "displayName": "String",
  "id": "String (identifier)",
  "loginWebUrl": "String",
  "longLogoWebUrlForDarkTheme": "String",
  "longLogoWebUrlForLightTheme": "String",
  "squareLogoWebUrlForDarkTheme": "String",
  "squareLogoWebUrlForLightTheme": "String",
  "isCourseActivitySyncEnabled": "Boolean"
}
```
