<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The group policy configuration entity contains the configured values for one or more group policy definitions.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-list?view=graph-rest-beta) | [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) objects. |
| [Get groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-get?view=graph-rest-beta) | [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) object. |
| [Create groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-create?view=graph-rest-beta) | [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) | Create a new [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) object. |
| [Delete groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta). |
| [Update groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-update?view=graph-rest-beta) | [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) | Update the properties of a [groupPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfiguration?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-assign?view=graph-rest-beta) | [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) collection |  |
| [updateDefinitionValues action](https://learn.microsoft.com/en-us/graph/api/intune-grouppolicy-grouppolicyconfiguration-updatedefinitionvalues?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time the object was created. |
| displayName | String | User provided name for the resource object. |
| description | String | User provided description for the resource object. |
| roleScopeTagIds | String collection | The list of scope tags for the configuration. |
| policyConfigurationIngestionType | [groupPolicyConfigurationIngestionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationingestiontype?view=graph-rest-beta) | Type of definitions configured for this policy. Possible values are: `unknown`, `custom`, `builtIn`, `mixed`, `unknownFutureValue`. |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | The date and time the entity was last modified. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definitionValues | [groupPolicyDefinitionValue](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicydefinitionvalue?view=graph-rest-beta) collection | The list of enabled or disabled group policy definition values for the configuration. |
| assignments | [groupPolicyConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-grouppolicy-grouppolicyconfigurationassignment?view=graph-rest-beta) collection | The list of group assignments for the configuration. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyConfiguration",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "roleScopeTagIds": [
    "String"
  ],
  "policyConfigurationIngestionType": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
