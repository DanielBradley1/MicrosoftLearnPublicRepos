<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# targetedManagedAppConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Configuration used to deliver a set of custom settings as-is to all users in the targeted security group

Inherits from [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List targetedManagedAppConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-list?view=graph-rest-1.0) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) objects. |
| [Get targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-get?view=graph-rest-1.0) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) object. |
| [Create targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-create?view=graph-rest-1.0) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) | Create a new [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) object. |
| [Delete targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0). |
| [Update targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-update?view=graph-rest-1.0) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) | Update the properties of a [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedappconfiguration?view=graph-rest-1.0) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-assign?view=graph-rest-1.0) | None |  |
| [targetApps action](https://learn.microsoft.com/en-us/graph/api/intune-mam-targetedmanagedappconfiguration-targetapps?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| customSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyvaluepair?view=graph-rest-1.0) collection | A set of string key and string value pairs to be sent to apps for users to whom the configuration is scoped, unalterned by this service Inherited from [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-1.0) |
| deployedAppCount | Int32 | Count of apps to which the current policy is deployed. |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| apps | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) collection | List of apps to which the policy is deployed. |
| deploymentSummary | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0) | Navigation property to deployment summary of the configuration. |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-1.0) collection | Navigation property to list of inclusion and exclusion groups to which the policy is deployed. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.targetedManagedAppConfiguration",
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
  ],
  "deployedAppCount": 1024,
  "isAssigned": true
}
```
