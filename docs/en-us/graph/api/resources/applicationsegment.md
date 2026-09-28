<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationsegment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-23 -->

# applicationSegment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that exposes properties for configuring allowed segment configurations for on-premises wildcard apps published through Microsoft Entra application proxy. The following types are derived from this abstract type:

- [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta)
- [ipApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/ipapplicationsegment?view=graph-rest-beta)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier that is assigned to an application segment by Microsoft Entra ID. Not nullable. Read-only. Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.applicationSegment",
  "id": "String (identifier)"
}
```
