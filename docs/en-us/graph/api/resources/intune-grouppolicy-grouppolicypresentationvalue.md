<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyPresentationValue resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The base presentation value entity that stores the value for a single group policy presentation.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyPresentationValues](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvalue-list?view=graph-rest-beta) | [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) objects. |
| [Get groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvalue-get?view=graph-rest-beta) | [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) object. |
| [Create groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvalue-create?view=graph-rest-beta) | [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) | Create a new [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) object. |
| [Delete groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvalue-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta). |
| [Update groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicypresentationvalue-update?view=graph-rest-beta) | [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) | Update the properties of a [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastModifiedDateTime | DateTimeOffset | The date and time the object was last modified. |
| createdDateTime | DateTimeOffset | The date and time the object was created. |
| id | String | Key of the entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitionValue | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) | The group policy definition value associated with the presentation value. |
| presentation | [groupPolicyPresentation](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentation?view=graph-rest-beta) | The group policy presentation associated with the presentation value. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyPresentationValue",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)"
}
```
