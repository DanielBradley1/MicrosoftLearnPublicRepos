<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# policyAssignment resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a read-only assignment that associates a Windows Autopatch policy with a device.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List policyAssignments](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-policyassignments?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta) collection | List policy assignments and their associated devices. |
| [Get policy assignment](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policyassignment-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyassignment?view=graph-rest-beta) | Read the properties and relationships of a policy assignment. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureAdDeviceId | String | The Microsoft Entra identifier of the assigned device. Read-only. |
| id | String | The unique identifier for the assignment. Read-only. |
| policyId | String | The identifier of the assigned Windows Autopatch policy. Read-only. |
| policyName | String | The display name of the assigned Windows Autopatch policy. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceProfile | [microsoft.graph.windowsUpdates.deviceProfile](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deviceprofile?view=graph-rest-beta) | The profile of the assigned device. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.policyAssignment",
  "azureAdDeviceId": "String",
  "id": "String (identifier)",
  "policyId": "String",
  "policyName": "String"
}
```
