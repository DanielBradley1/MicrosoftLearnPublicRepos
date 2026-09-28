<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# educationClass resource type

Namespace: microsoft.graph

Represents a class within a school. The **educationClass** resource corresponds to the Microsoft 365 group and shares the same ID. Students are regular members of the class, and teachers are owners and have appropriate rights. For Office experiences to work correctly, teachers must be members of both the teachers and members collections.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List classes](https://learn.microsoft.com/en-us/graph/api/educationclass-list?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Get a list of the [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) objects and their properties. |
| [List modules](https://learn.microsoft.com/en-us/graph/api/educationclass-list-modules?view=graph-rest-1.0) | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0)collection | Get an **educationModule** object collection. |
| [Create class](https://learn.microsoft.com/en-us/graph/api/educationclass-post?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) | Create a new [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object. |
| [Get class](https://learn.microsoft.com/en-us/graph/api/educationclass-get?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) | Read the properties and relationships of an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object. |
| [Update class](https://learn.microsoft.com/en-us/graph/api/educationclass-update?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) | Update the properties of an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object. |
| [Delete class](https://learn.microsoft.com/en-us/graph/api/educationclass-delete?view=graph-rest-1.0) | None | Delete an [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) object. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/educationclass-delta?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Get incremental changes for **educationClasses**. |
| [Get recently modified submissions](https://learn.microsoft.com/en-us/graph/api/educationclass-getrecentlymodifiedsubmissions?view=graph-rest-1.0) | [educationSubmission](https://learn.microsoft.com/en-us/graph/api/resources/educationsubmission?view=graph-rest-1.0) collection | Retrieve submissions modified in the previous seven days. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classCode | String | Class code used by the school to identify the class. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Entity who created the class |
| description | String | Description of the class. |
| displayName | String | Name of the class. |
| externalId | String | ID of the class from the syncing system. |
| externalSource | educationExternalSource | How this class was created. The possible values are: `sis`, `manual`. |
| externalSourceDetail | String | The name of the external source this resource was generated from. |
| externalName | String | Name of the class in the syncing system. |
| grade | String | Grade level of the class. |
| id | String | Object identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| mailNickname | String | Mail name for sending email to all members, if this is enabled. |
| term | [educationTerm](https://learn.microsoft.com/en-us/graph/api/resources/educationterm?view=graph-rest-1.0) | Term for this class. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [educationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/educationassignment?view=graph-rest-1.0) collection | All assignments associated with this class. Nullable. |
| assignmentCategories | [educationCategory](https://learn.microsoft.com/en-us/graph/api/resources/educationcategory?view=graph-rest-1.0) collection | All categories associated with this class. Nullable. |
| assignmentDefaults | [educationAssignmentDefaults](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentdefaults?view=graph-rest-1.0) collection | Specifies class-level defaults respected by new assignments created in the class. |
| assignmentSettings | [educationAssignmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentsettings?view=graph-rest-1.0) collection | Specifies class-level assignments settings. |
| group | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | The underlying Microsoft 365 group object. |
| members | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | All users in the class. Nullable. |
| modules | [educationModule](https://learn.microsoft.com/en-us/graph/api/resources/educationmodule?view=graph-rest-1.0) collection | All modules in the class. Nullable. |
| schools | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) collection | All schools that this class is associated with. Nullable. |
| teachers | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | All teachers in the class. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationClass",
  "description": "String",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "classCode": "String",
  "externalName": "String",
  "externalId": "String",
  "externalSource": "String",
  "externalSourceDetail": "String",
  "grade": "String",
  "id": "String (identifier)",
  "mailNickname": "String",
  "term": {
    "@odata.type": "microsoft.graph.educationTerm"
  }
}
```
