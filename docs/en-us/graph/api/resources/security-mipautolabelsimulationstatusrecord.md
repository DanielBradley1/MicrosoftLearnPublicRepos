<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mipautolabelsimulationstatusrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# mipAutoLabelSimulationStatusRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures status information for Microsoft Information Protection \(MIP\) auto-labeling simulation runs. This resource provides details about the current state, progress, and execution status of simulation runs used to evaluate auto-labeling policies without actually applying labels to content. Simulation status records help administrators track and monitor the execution of auto-labeling simulations across their organization.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mipAutoLabelSimulationStatusRecord"
}
```
