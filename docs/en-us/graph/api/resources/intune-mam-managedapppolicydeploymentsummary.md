<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# managedAppPolicyDeploymentSummary resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The ManagedAppEntity is the base entity type for all other entity types under app management workflow.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapppolicydeploymentsummary-get?view=graph-rest-1.0) | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0) | Read properties and relationships of the [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0) object. |
| [Update managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedapppolicydeploymentsummary-update?view=graph-rest-1.0) | [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0) | Update the properties of a [managedAppPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummary?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String |  |
| configurationDeployedUserCount | Int32 |  |
| lastRefreshTime | DateTimeOffset |  |
| configurationDeploymentSummaryPerApp | [managedAppPolicyDeploymentSummaryPerApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummaryperapp?view=graph-rest-1.0) collection |  |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppPolicyDeploymentSummary",
  "displayName": "String",
  "configurationDeployedUserCount": 1024,
  "lastRefreshTime": "String (timestamp)",
  "configurationDeploymentSummaryPerApp": [
    {
      "@odata.type": "microsoft.graph.managedAppPolicyDeploymentSummaryPerApp",
      "mobileAppIdentifier": {
        "@odata.type": "microsoft.graph.androidMobileAppIdentifier",
        "packageId": "String"
      },
      "configurationAppliedUserCount": 1024
    }
  ],
  "id": "String (identifier)",
  "version": "String"
}
```
