<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the deployment summary of a WindowsDefenderApplicationControl supplemental policy.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary-get?view=graph-rest-beta) | [windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary?view=graph-rest-beta) | Read properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary?view=graph-rest-beta) object. |
| [Update windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary-update?view=graph-rest-beta) | [windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary?view=graph-rest-beta) | Update the properties of a [windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicydeploymentsummary?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| deployedDeviceCount | Int32 | Number of Devices that have successfully deployed this WindowsDefenderApplicationControl supplemental policy. |
| failedDeviceCount | Int32 | Number of Devices that have failed to deploy this WindowsDefenderApplicationControl supplemental policy. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDefenderApplicationControlSupplementalPolicyDeploymentSummary",
  "id": "String (identifier)",
  "deployedDeviceCount": 1024,
  "failedDeviceCount": 1024
}
```
