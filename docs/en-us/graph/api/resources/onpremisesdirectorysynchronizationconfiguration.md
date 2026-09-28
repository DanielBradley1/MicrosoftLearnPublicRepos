<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronizationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-03 -->

# onPremisesDirectorySynchronizationConfiguration resource type

Namespace: microsoft.graph

Consists of configurations that can be fine-tuned and impact the [on-premises directory synchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization?view=graph-rest-1.0) process for a tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accidentalDeletionPrevention | [onPremisesAccidentalDeletionPrevention](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesaccidentaldeletionprevention?view=graph-rest-1.0) | Contains the accidental deletion prevention configuration for a tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesDirectorySynchronizationConfiguration",
  "accidentalDeletionPrevention": {
    "@odata.type": "microsoft.graph.onPremisesAccidentalDeletionPrevention"
  }
}
```
