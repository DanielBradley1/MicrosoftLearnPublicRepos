<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# targetedManagedAppConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Configuration used to deliver a set of custom settings as-is to all users in the targeted security group

Inherits from [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List targetedManagedAppConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-list?view=graph-rest-beta) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) objects. |
| [Get targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-get?view=graph-rest-beta) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) | Read properties and relationships of the [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) object. |
| [Create targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-create?view=graph-rest-beta) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) | Create a new [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) object. |
| [Delete targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-delete?view=graph-rest-beta) | None | Deletes a [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta). |
| [Update targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-update?view=graph-rest-beta) | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) | Update the properties of a [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) object. |
| **Mobile app management \(MAM\)** |  |  |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-assign?view=graph-rest-beta) | None |  |
| [targetApps action](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-targetapps?view=graph-rest-beta) | None |  |
| **Policy Set** |  |  |
| [hasPayloadLinks action](https://learn.microsoft.com/en-us/graph/api/intune-shared-targetedmanagedappconfiguration-haspayloadlinks?view=graph-rest-beta) | [hasPayloadLinkResultItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| customSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyvaluepair?view=graph-rest-beta) collection | A set of string key and string value pairs to be sent to apps for users to whom the configuration is scoped, unalterned by this service Inherited from [managedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappconfiguration?view=graph-rest-beta) |
| deployedAppCount | Int32 | Count of apps to which the current policy is deployed. |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Mobile app management \(MAM\)** |  |  |
| apps | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-beta) collection | List of apps to which the policy is deployed. |
| deploymentSummary | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-beta) | Navigation property to deployment summary of the configuration. |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-beta) collection | Navigation property to list of inclusion and exclusion groups to which the policy is deployed. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.targetedManagedAppConfiguration",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
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
