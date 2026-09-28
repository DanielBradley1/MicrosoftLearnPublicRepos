<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-enrichment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# enrichment resource type

Namespace: microsoft.graph.healthMonitoring

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents more context for an [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert?view=graph-rest-beta) in Microsoft Entra Health monitoring.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| impacts | [microsoft.graph.healthMonitoring.resourceImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-resourceimpactsummary?view=graph-rest-beta) collection | A collection of resource impact summaries that gives a high level view of the kind of resources that were impacted and to what degree. |
| state | microsoft.graph.healthMonitoring.enrichmentState | The current enrichment state of the alert. The possible values are: `none`, `inProgress`, `enriched`, `unknownFutureValue`. |
| supportingData | [microsoft.graph.healthMonitoring.supportingData](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-supportingdata?view=graph-rest-beta) | A collection of supportingData locations that can be queried for debugging the alert. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.healthMonitoring.enrichment",
  "state": "String",
  "impacts": [
    {
      "@odata.type": "microsoft.graph.healthMonitoring.resourceImpactSummary"
    }
  ],
  "supportingData": {
    "@odata.type": "microsoft.graph.healthMonitoring.supportingData"
  }
}
```
