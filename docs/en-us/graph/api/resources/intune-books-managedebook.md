<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# managedEBook resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An abstract class containing the base properties for Managed eBook.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedEBooks](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebook-list?view=graph-rest-1.0) | [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) collection | List properties and relationships of the [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) objects. |
| [Get managedEBook](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebook-get?view=graph-rest-1.0) | [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) | Read properties and relationships of the [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-books-managedebook-assign?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| displayName | String | Name of the eBook. |
| description | String | Description. |
| publisher | String | Publisher. |
| publishedDateTime | DateTimeOffset | The date and time when the eBook was published. |
| largeCover | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-1.0) | Book cover. |
| createdDateTime | DateTimeOffset | The date and time when the eBook file was created. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the eBook was last modified. |
| informationUrl | String | The more information Url. |
| privacyInformationUrl | String | The privacy statement Url. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) collection | The list of assignments for this eBook. |
| installSummary | [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) | Mobile App Install Summary. |
| deviceStates | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) collection | The list of installation states for this eBook. |
| userStateSummary | [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) collection | The list of installation states for this eBook. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedEBook",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "publisher": "String",
  "publishedDateTime": "String (timestamp)",
  "largeCover": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "informationUrl": "String",
  "privacyInformationUrl": "String"
}
```
