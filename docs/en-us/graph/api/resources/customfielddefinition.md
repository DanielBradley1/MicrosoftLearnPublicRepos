<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# customFieldDefinition resource type \(planner\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A custom field defined on a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), used to capture structured, plan-specific data on [tasks](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta). Choice options for single-choice and multiple-choice fields are contained under `choiceOptions`; values are set per task via [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta).

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-customfielddefinitions?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) collection | Get a list of the customFieldDefinition objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-customfielddefinitions?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) | Create a new customFieldDefinition object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-get?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) | Read the properties and relationships of [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-update?view=graph-rest-beta) | [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/customfielddefinition?view=graph-rest-beta) | Update the properties of a customFieldDefinition object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-customfielddefinitions?view=graph-rest-beta) | None | Delete a customFieldDefinition object. |
| [List choiceOptions](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-list-choiceoptions?view=graph-rest-beta) | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) collection | Get a list of the customChoiceOption objects and their properties. |
| [Create customChoiceOption](https://learn.microsoft.com/en-us/graph/api/customfielddefinition-post-choiceoptions?view=graph-rest-beta) | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) | Create a new customChoiceOption object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who created the entity. Read-only. |
| createdDateTime | DateTimeOffset | Date and time the entity was created. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| deletedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who deleted the custom field definition, if it was deleted. |
| deletedDateTime | DateTimeOffset | Date and time the custom field definition was deleted, if applicable. |
| displayName | String | Name of the custom field. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| planId | String | ID of the plan the custom field is defined on. Required, and immutable after creation. |
| rollupType | customFieldRollupType | How values of this custom field are rolled up across tasks. The possible values are: `noRollup`, `max`, `min`, `sum`, `average`, `unknownFutureValue`. |
| valueType | customFieldValueType | Data type of the custom field's values.. The possible values are: `text`, `date`, `utcDateTime`, `number`, `decimal`, `flag`, `singleChoiceText`, `multipleChoiceText`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| choiceOptions | [customChoiceOption](https://learn.microsoft.com/en-us/graph/api/resources/customchoiceoption?view=graph-rest-beta) collection | The collection of selectable choice options for a single-choice or multiple-choice custom field. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customFieldDefinition",
  "id": "String (identifier)",
  "planId": "String",
  "displayName": "String",
  "valueType": "String",
  "rollupType": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "deletedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "deletedDateTime": "String (timestamp)",
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  }
}
```
