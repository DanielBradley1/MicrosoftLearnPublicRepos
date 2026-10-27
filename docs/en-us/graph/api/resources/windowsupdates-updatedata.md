<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatedata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# updateData resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides a read-only entry point for Windows Autopatch device, policy assignment, applicability, and driver reporting data. Access this resource through the **data** relationship of [adminWindowsUpdates](https://learn.microsoft.com/en-us/graph/api/resources/adminwindowsupdates?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List applicableCatalogSummaries](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-applicablecatalogsummaries?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableCatalogSummary](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalogsummary?view=graph-rest-beta) collection | List catalog applicability aggregated across Autopatch policies. |
| [List deviceProfiles](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-deviceprofiles?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deviceProfile](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deviceprofile?view=graph-rest-beta) collection | List device profile and servicing information. |
| [List drivers](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-drivers?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.driverUpdateReport](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatereport?view=graph-rest-beta) collection | List driver updates available in the tenant. |
| [List policyAssignments](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-policyassignments?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta) collection | List policy-to-device assignments. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applicableCatalogSummaries | [microsoft.graph.windowsUpdates.applicableCatalogSummary](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalogsummary?view=graph-rest-beta) collection | Catalog applicability aggregated across Autopatch policies. Read-only. |
| deviceProfiles | [microsoft.graph.windowsUpdates.deviceProfile](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deviceprofile?view=graph-rest-beta) collection | Device profile and Windows servicing information. Read-only. |
| drivers | [microsoft.graph.windowsUpdates.driverUpdateReport](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatereport?view=graph-rest-beta) collection | Driver updates available in the tenant and their per-device rollout status. Read-only. |
| policyAssignments | [microsoft.graph.windowsUpdates.policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta) collection | Assignments that associate Autopatch policies with devices. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updateData"
}
```
