<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpolicypendingapplystatusresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-23 -->

# cloudPcPolicyPendingApplyStatusResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the result of checking whether a provisioning policy has unapplied changes pending for Cloud PCs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasUnappliedPolicyUpdate | Boolean | Indicates whether the provisioning policy has unapplied changes pending for Cloud PCs. When `true`, the policy contains changes that aren't yet applied. When `false`, all policy changes are applied. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcPolicyPendingApplyStatusResult",
  "hasUnappliedPolicyUpdate": true
}
```
