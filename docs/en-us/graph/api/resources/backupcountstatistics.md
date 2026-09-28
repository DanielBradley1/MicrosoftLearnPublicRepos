<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/backupcountstatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# backupCountStatistics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the count of artifacts in each of the protection stages.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastComputedDateTime | DateTimeOffset | The date and time when this metric was calculated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| offboardRequested | Int32 | The count of artifacts in **offboardRequested** state. This metric captures artifacts in protection‑unit–level offboarding and artifacts offboarded due to an unhealthy billing profile. |
| protectedCompleted | Int32 | The count of artifacts in protected state. |
| protectedFailed | Int32 | The count of artifacts whose protection was attempted but failed. These artifacts typically have unprotected as their status. |
| protectedInProgress | Int32 | The count of artifacts whose protection attempt is currently in progress. This metric applies to artifacts for which the process to start or resume taking backups is still required. |
| removed | Int32 | The count of artifacts not associated with any policy. This property is always `null` for a policy-level report. Nullable. |
| total | Int32 | The count of artifacts in the specified entity. The currently supported entity is a backup policy. |
| unprotectedCompleted | Int32 | The count of artifacts that are no longer actively protected. These artifacts have historical restore points, but no new backups are being taken. |
| unprotectedFailed | Int32 | The count of artifacts for which unprotection was attempted but didn't complete. These artifacts are typically in the protected state. |
| unprotectedInProgress | Int32 | The count of artifacts for which unprotection is currently in progress. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.backupCountStatistics",
  "lastComputedDateTime": "String (timestamp)",
  "offboardRequested": "Int32",
  "protectedCompleted": "Int32",
  "protectedFailed": "Int32",
  "protectedInProgress": "Int32",
  "removed": "Int32",
  "total": "Int32",
  "unprotectedCompleted": "Int32",
  "unprotectedFailed": "Int32",
  "unprotectedInProgress": "Int32"
}
```
