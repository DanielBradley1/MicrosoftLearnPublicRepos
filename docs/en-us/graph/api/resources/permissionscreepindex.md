<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindex?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsCreepIndex resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Assigns a score based on an identities excessive permissions that is classified into three buckets: 0-33: low, 34-66: medium, 67-100: high.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| score | Int32 | This value represents how much risk an identity poses. This risk range is classified in three buckets: 0-33: low, 34-66: medium, 67-100: high.. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsCreepIndex",
  "score": "Integer"
}
```
