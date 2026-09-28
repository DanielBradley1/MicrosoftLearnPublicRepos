<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationValueText resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The entity represents a string value for a drop-down list, combo box, or text box presentation on a policy definition.

Inherits from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationValueTexts](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluetext-list?view=graph-rest-beta) | [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluetext-get?view=graph-rest-beta) | [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluetext-create?view=graph-rest-beta) | [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) | Create a new [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluetext-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta). |
| [Update groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluetext-update?view=graph-rest-beta) | [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationValueText](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluetext?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastModifiedDateTime | DateTimeOffset | The date and time the object was last modified. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the object was created. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| value | String | A string value for the associated presentation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitionValue | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) | The group policy definition value associated with the presentation value. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| presentation | [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) | The group policy presentation associated with the presentation value. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationValueText",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "value": "String"
}
```
