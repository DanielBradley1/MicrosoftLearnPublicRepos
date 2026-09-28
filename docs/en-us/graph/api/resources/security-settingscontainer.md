<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-settingscontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-10 -->

# settingsContainer resource type

Namespace: microsoft.graph.security

Represents a container for security identities APIs that currently exposes the [autoAuditingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0) relationship.

## Methods

None

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| autoAuditingConfiguration | [microsoft.graph.security.autoAuditingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-autoauditingconfiguration?view=graph-rest-1.0) | Represents automatic configuration for collection of Windows event logs as needed for Defender for Identity sensors. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.settingsContainer"
}
```
