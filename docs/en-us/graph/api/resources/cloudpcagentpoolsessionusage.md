<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolsessionusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcAgentPoolSessionUsage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the session usage of a Cloud PC agent pool.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeSessionsCount | Int32 | The number of active sessions in the pool. Read-only. |
| availableSessionsCount | Int32 | The number of available sessions in the pool. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolSessionUsage",
  "activeSessionsCount": "Int32",
  "availableSessionsCount": "Int32"
}
```
