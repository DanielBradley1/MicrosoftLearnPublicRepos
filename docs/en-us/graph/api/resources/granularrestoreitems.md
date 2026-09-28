<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/granularrestoreitems?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# granularRestoreItems enum type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates the type of granular restore items that can be searched and restored from backup.

## Members

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations).

| Member | Description |
| :--- | :--- |
| email | Email message item. |
| note | Note item. |
| contact | Contact item. |
| task | Task item. |
| calendar | Calendar item. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.granularRestoreItems"
}
```
