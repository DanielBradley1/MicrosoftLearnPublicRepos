<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/actionsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# actionSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

This will contain information on the number of authorization system actions that have been granted to an identity and the number of actions executed by this identity in the last 90 days.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assigned | Int32 | This is the number of authorization system actions that have been assigned to the identity. |
| available | Int32 | This is the number of authorization system actions that the identity has exercised in the last 90 days. |
| exercised | Int32 | This is the maximum number of actions that are available in the authorization system. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.actionSummary",
  "assigned": "Integer",
  "exercised": "Integer",
  "available": "Integer"
}
```
