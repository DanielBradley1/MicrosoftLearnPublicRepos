<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-containerfilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# containerFilter resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines how certain containers, such as organizational units, should be considered in scope for a [synchronizationRule](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationrule?view=graph-rest-beta) \(**containerFilter** property\). This object is only used by Azure Active Directory Connect cloud sync scenarios.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includedContainers | String collection | The identifiers of containers, such as organizational units, that are in scope for a synchronization rule. For Active Directory organizational units, use the distinguished names. An empty list means no container filtering is configured. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.containerFilter",
  "includedContainers": [
    "String"
  ]
}
```
