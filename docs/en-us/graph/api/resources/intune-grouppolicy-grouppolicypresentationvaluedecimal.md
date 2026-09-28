<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationValueDecimal resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The entity represents an unsigned integer value of a decimal text box presentation on a policy definition.

Inherits from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationValueDecimals](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluedecimal-list?view=graph-rest-beta) | [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluedecimal-get?view=graph-rest-beta) | [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluedecimal-create?view=graph-rest-beta) | [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) | Create a new [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluedecimal-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta). |
| [Update groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvaluedecimal-update?view=graph-rest-beta) | [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationValueDecimal](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvaluedecimal?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastModifiedDateTime | DateTimeOffset | The date and time the object was last modified. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the object was created. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| value | Int64 | An unsigned integer value for the associated presentation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitionValue | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) | The group policy definition value associated with the presentation value. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |
| presentation | [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) | The group policy presentation associated with the presentation value. Inherited from [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationValueDecimal",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "value": 1024
}
```
