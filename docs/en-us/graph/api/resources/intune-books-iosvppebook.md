<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosVppEBook resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties for iOS Vpp eBook.

Inherits from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosVppEBooks](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebook-list?view=graph-rest-1.0) | [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) collection | List properties and relationships of the [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) objects. |
| [Get iosVppEBook](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebook-get?view=graph-rest-1.0) | [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) | Read properties and relationships of the [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) object. |
| [Create iosVppEBook](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebook-create?view=graph-rest-1.0) | [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) | Create a new [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) object. |
| [Delete iosVppEBook](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebook-delete?view=graph-rest-1.0) | None | Deletes a [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0). |
| [Update iosVppEBook](https://learn.microsoft.com/en-us/graph/api/intune-books-iosvppebook-update?view=graph-rest-1.0) | [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) | Update the properties of a [iosVppEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-iosvppebook?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| displayName | String | Name of the eBook. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| description | String | Description. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| publisher | String | Publisher. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| publishedDateTime | DateTimeOffset | The date and time when the eBook was published. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| largeCover | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-1.0) | Book cover. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time when the eBook file was created. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | The date and time when the eBook was last modified. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| informationUrl | String | The more information Url. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| privacyInformationUrl | String | The privacy statement Url. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| vppTokenId | Guid | The Vpp token ID. |
| appleId | String | The Apple ID associated with Vpp token. |
| vppOrganizationName | String | The Vpp token's organization name. |
| genres | String collection | Genres. |
| language | String | Language. |
| seller | String | Seller. |
| totalLicenseCount | Int32 | Total license count. |
| usedLicenseCount | Int32 | Used license count. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [managedEBookAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookassignment?view=graph-rest-1.0) collection | The list of assignments for this eBook. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| installSummary | [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) | Mobile App Install Summary. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| deviceStates | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) collection | The list of installation states for this eBook. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |
| userStateSummary | [userInstallStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-userinstallstatesummary?view=graph-rest-1.0) collection | The list of installation states for this eBook. Inherited from [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosVppEBook",
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
  "privacyInformationUrl": "String",
  "vppTokenId": "Guid",
  "appleId": "String",
  "vppOrganizationName": "String",
  "genres": [
    "String"
  ],
  "language": "String",
  "seller": "String",
  "totalLicenseCount": 1024,
  "usedLicenseCount": 1024
}
```
