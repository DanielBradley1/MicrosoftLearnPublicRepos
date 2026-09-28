<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingsensitivitylabelassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-23 -->

# onlineMeetingSensitivityLabelAssignment resource type

Namespace: microsoft.graph

Contains information about the sensitivity label applied to the Teams meeting in Microsoft Graph. This object corresponds to the label that is created and managed by admins in Microsoft Purview and is used to enforce data protection and meeting governance.

For more information, see [Teams meetings with protection for sensitive data](https://learn.microsoft.com/en-us/microsoftteams/configure-meetings-sensitive-protection).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sensitivityLabelId | String | The ID of the sensitivity label that is applied to the Teams meeting. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onlineMeetingSensitivityLabelAssignment",
  "sensitivityLabelId": "String"
}
```
