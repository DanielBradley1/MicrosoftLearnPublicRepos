<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignedlabel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# assignedLabel resource type

Namespace: microsoft.graph

Represents a sensitivity label assigned to a Microsoft 365 group. Administrators publish sensitivity labels in the Microsoft 365 Security and Compliance Center as part of Microsoft Purview Information Protection capabilities. For more information about sensitivity labels, see [Sensitivity labels overview](https://learn.microsoft.com/en-us/microsoft-365/compliance/sensitivity-labels).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the label. Read-only. |
| labelId | String | The unique identifier of the label. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "labelId": "String"
}
```
