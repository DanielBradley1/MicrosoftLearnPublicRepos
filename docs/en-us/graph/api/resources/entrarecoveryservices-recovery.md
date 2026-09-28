<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recovery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-15 -->

# recovery resource type

Namespace: microsoft.graph.entraRecoveryServices

Represents the entry point for the Microsoft Entra Backup and Recovery service. Provides access to snapshots and recovery jobs for a tenant, enabling administrators to restore directory objects to a previous state.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| jobs | [microsoft.graph.entraRecoveryServices.recoveryJobBase](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjobbase?view=graph-rest-1.0) collection | Collection of all recovery jobs \(both preview and recovery\) for the tenant. |
| snapshots | [microsoft.graph.entraRecoveryServices.snapshot](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-snapshot?view=graph-rest-1.0) collection | Collection of backup snapshots available for the tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entraRecoveryServices.recovery"
}
```
