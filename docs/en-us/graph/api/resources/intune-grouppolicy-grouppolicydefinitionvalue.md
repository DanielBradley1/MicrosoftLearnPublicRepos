<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyDefinitionValue resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The definition value entity stores the value for a single group policy definition.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyDefinitionValues](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinitionvalue-list?view=graph-rest-beta) | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) objects. |
| [Get groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinitionvalue-get?view=graph-rest-beta) | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) object. |
| [Create groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinitionvalue-create?view=graph-rest-beta) | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) | Create a new [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) object. |
| [Delete groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinitionvalue-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta). |
| [Update groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicydefinitionvalue-update?view=graph-rest-beta) | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) | Update the properties of a [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time the object was created. |
| enabled | Boolean | Enables or disables the associated group policy definition. |
| configurationType | [groupPolicyConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationtype?view=graph-rest-beta) | Specifies how the value should be configured. This can be either as a Policy or as a Preference. Possible values are: `policy`, `preference`. |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| presentationValues | [groupPolicyPresentationValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicypresentationvalue?view=graph-rest-beta) collection | The associated group policy presentation values with the definition value. |
| definition | [groupPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinition?view=graph-rest-beta) | The associated group policy definition with the value. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyDefinitionValue",
  "createdDateTime": "String (timestamp)",
  "enabled": true,
  "configurationType": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
