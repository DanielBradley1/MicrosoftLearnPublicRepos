<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcentrauserdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# cloudPcEntraUserDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the user details \(for example, ID and display name\) for a user associated with a Reserve Cloud PC assignment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userDisplayName | String | The display name of the user. Read-only. |
| userId | String | The unique identifier \(GUID\) of the user. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcEntraUserDetail",
  "userDisplayName": "String",
  "userId": "String"
}
```
