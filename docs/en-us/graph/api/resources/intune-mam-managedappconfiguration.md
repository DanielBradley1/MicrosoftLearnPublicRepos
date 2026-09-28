<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Configuration used to deliver a set of custom settings as-is to apps for users to whom the configuration is scoped

Inherits from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedAppConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappconfiguration-list?view=graph-rest-1.0) | [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0) objects. |
| [Get managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappconfiguration-get?view=graph-rest-1.0) | [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| customSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyvaluepair?view=graph-rest-1.0) collection | A set of string key and string value pairs to be sent to apps for users to whom the configuration is scoped, unalterned by this service |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppConfiguration",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "version": "String",
  "customSettings": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ]
}
```
