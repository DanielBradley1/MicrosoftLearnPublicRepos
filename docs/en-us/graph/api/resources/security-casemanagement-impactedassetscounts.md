<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-impactedassetscounts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# impactedAssetsCounts resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains impacted asset count summaries for an [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta). Returned in the **impactedAssets** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aiAgents | Int32 | The number of impacted AI agents. |
| apps | Int32 | The number of impacted apps. |
| cloudResources | Int32 | The number of impacted cloud resources. |
| files | Int32 | The number of impacted files. |
| ips | Int32 | The number of impacted IP addresses. |
| machines | Int32 | The number of impacted machines. |
| mailboxes | Int32 | The number of impacted mailboxes. |
| oauthApps | Int32 | The number of impacted OAuth apps. |
| processes | Int32 | The number of impacted processes. |
| registryKeys | Int32 | The number of impacted registry keys. |
| securityGroups | Int32 | The number of impacted security groups. |
| total | Int32 | The total number of impacted assets. |
| urls | Int32 | The number of impacted URLs. |
| users | Int32 | The number of impacted users. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.impactedAssetsCounts",
  "machines": "Integer",
  "users": "Integer",
  "mailboxes": "Integer",
  "apps": "Integer",
  "cloudResources": "Integer",
  "aiAgents": "Integer",
  "ips": "Integer",
  "urls": "Integer",
  "files": "Integer",
  "processes": "Integer",
  "registryKeys": "Integer",
  "securityGroups": "Integer",
  "oauthApps": "Integer",
  "total": "Integer"
}
```
