<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcentragroupdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# cloudPcEntraGroupDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Microsoft Entra group details \(for example, ID and display name\) for the Entra ID group associated with a user's Reserve Cloud PC assignment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| groupDisplayName | String | The display name of the Microsoft Entra ID group. Read-only. |
| groupId | String | The unique identifier \(GUID\) of the Microsoft Entra ID group. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcEntraGroupDetail",
  "groupDisplayName": "String",
  "groupId": "String"
}
```
