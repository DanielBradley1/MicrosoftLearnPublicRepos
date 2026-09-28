<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# educationSchool resource type

Namespace: microsoft.graph

A resource representing a school and used to manage the classes, teachers, and students of the represented school.

Inherits from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List schools](https://learn.microsoft.com/en-us/graph/api/educationschool-list?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) collection | Get a list of the [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) objects and their properties. |
| [Create school](https://learn.microsoft.com/en-us/graph/api/educationschool-post?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) | Create a new [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object. |
| [Get school](https://learn.microsoft.com/en-us/graph/api/educationschool-get?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) | Read the properties and relationships of an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object. |
| [Update school](https://learn.microsoft.com/en-us/graph/api/educationschool-update?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) | Update the properties of an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object. |
| [Delete school](https://learn.microsoft.com/en-us/graph/api/educationschool-delete?view=graph-rest-1.0) | None | Delete an [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) object. |
| [Get changes to schools](https://learn.microsoft.com/en-us/graph/api/educationschool-delta?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) collection | Get incremental changes to the resource collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | Address of the school. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Entity who created the school. |
| description | String | Description of the school. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). |
| displayName | String | Display name of the school. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). |
| externalId | String | ID of school in syncing system. |
| externalPrincipalId | String | ID of principal in syncing system. |
| externalSource | educationExternalSource | Source where this organization was created from. Inherited from [educationOrganization](https://learn.microsoft.com/en-us/graph/api/resources/educationorganization?view=graph-rest-1.0). The possible values are: `sis`, `manual`. |
| externalSourceDetail | String | The name of the external source this resource was generated from. |
| highestGrade | String | Highest grade taught. |
| id | String | Object identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lowestGrade | String | Lowest grade taught. |
| phone | String | Phone number of school. |
| principalEmail | String | Email address of the principal. |
| principalName | String | Name of the principal. |
| schoolNumber | String | School Number. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| administrativeUnit | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | The underlying administrativeUnit for this school. |
| classes | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Classes taught at the school. Nullable. |
| users | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | Users in the school. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationSchool",
  "address": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "description": "String",
  "displayName": "String",
  "externalId": "String",
  "externalPrincipalId": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "highestGrade": "String",
  "id": "String (identifier)",
  "lowestGrade": "String",
  "phone": "String",
  "principalEmail": "String",
  "principalName": "String",
  "schoolNumber": "String"
}
```
