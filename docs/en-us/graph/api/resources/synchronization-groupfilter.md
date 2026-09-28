<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-groupfilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# groupFilter resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines how groups should be considered in scope for a [synchronizationRule](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-beta) \(**groupFilter** property\). This object is only used by Azure Active Directory Connect cloud sync scenarios.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includedGroups | String collection | Identifiers of groups that are in scope for a synchronization rule. For Active Directory groups, use the distinguished names. An empty list means no group filtering is configured. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupFilter",
  "includedGroups": [
    "String"
  ]
}
```
