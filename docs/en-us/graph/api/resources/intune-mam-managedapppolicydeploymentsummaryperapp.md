<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicydeploymentsummaryperapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppPolicyDeploymentSummaryPerApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents policy deployment summary per app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mobileAppIdentifier | [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-1.0) | Deployment of an app. |
| configurationAppliedUserCount | Int32 | Number of users the policy is applied. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppPolicyDeploymentSummaryPerApp",
  "mobileAppIdentifier": {
    "@odata.type": "microsoft.graph.androidMobileAppIdentifier",
    "packageId": "String"
  },
  "configurationAppliedUserCount": 1024
}
```
