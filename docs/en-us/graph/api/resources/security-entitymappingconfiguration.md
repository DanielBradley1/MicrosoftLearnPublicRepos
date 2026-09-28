<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-entitymappingconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# entityMappingConfiguration resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Holds the per-entity-type mappings that translate detection query columns into the entities that are attached to the resulting alert. This resource is configured in the **entityMappings** property of an [alertTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-alerttemplate?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accounts | [microsoft.graph.security.accountEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-accountentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to account entities attached to the alert. |
| amazonResources | [microsoft.graph.security.amazonResourceEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-amazonresourceentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to Amazon Web Services resource entities attached to the alert. |
| azureResources | [microsoft.graph.security.azureResourceEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-azureresourceentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to Azure resource entities attached to the alert. |
| cloudApplications | [microsoft.graph.security.cloudApplicationEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudapplicationentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to cloud application entities attached to the alert. |
| dns | [microsoft.graph.security.dnsEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-dnsentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to DNS entities attached to the alert. |
| files | [microsoft.graph.security.fileEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-fileentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to file entities attached to the alert. |
| googleCloudResources | [microsoft.graph.security.googleCloudResourceEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-googlecloudresourceentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to Google Cloud resource entities attached to the alert. |
| hosts | [microsoft.graph.security.hostEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-hostentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to host entities attached to the alert. |
| ips | [microsoft.graph.security.ipEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-ipentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to IP address entities attached to the alert. |
| mailboxes | [microsoft.graph.security.mailboxEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-mailboxentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to mailbox entities attached to the alert. |
| mailClusters | [microsoft.graph.security.mailClusterEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-mailclusterentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to mail cluster entities attached to the alert. |
| mailMessages | [microsoft.graph.security.mailMessageEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-mailmessageentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to mail message entities attached to the alert. |
| oAuthApplications | [microsoft.graph.security.oAuthApplicationEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-oauthapplicationentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to OAuth application entities attached to the alert. |
| processes | [microsoft.graph.security.processEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-processentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to process entities attached to the alert. |
| registryValues | [microsoft.graph.security.registryValueEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-registryvalueentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to registry value entities attached to the alert. |
| securityGroups | [microsoft.graph.security.securityGroupEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-securitygroupentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to security group entities attached to the alert. |
| urls | [microsoft.graph.security.urlEntityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-urlentitymapping?view=graph-rest-beta) collection | Mappings from detection query columns to URL entities attached to the alert. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.entityMappingConfiguration",
  "accounts": [
    { "@odata.type": "microsoft.graph.security.accountEntityMapping" }
  ],
  "amazonResources": [
    { "@odata.type": "microsoft.graph.security.amazonResourceEntityMapping" }
  ],
  "azureResources": [
    { "@odata.type": "microsoft.graph.security.azureResourceEntityMapping" }
  ],
  "cloudApplications": [
    { "@odata.type": "microsoft.graph.security.cloudApplicationEntityMapping" }
  ],
  "dns": [
    { "@odata.type": "microsoft.graph.security.dnsEntityMapping" }
  ],
  "files": [
    { "@odata.type": "microsoft.graph.security.fileEntityMapping" }
  ],
  "googleCloudResources": [
    { "@odata.type": "microsoft.graph.security.googleCloudResourceEntityMapping" }
  ],
  "hosts": [
    { "@odata.type": "microsoft.graph.security.hostEntityMapping" }
  ],
  "ips": [
    { "@odata.type": "microsoft.graph.security.ipEntityMapping" }
  ],
  "mailboxes": [
    { "@odata.type": "microsoft.graph.security.mailboxEntityMapping" }
  ],
  "mailClusters": [
    { "@odata.type": "microsoft.graph.security.mailClusterEntityMapping" }
  ],
  "mailMessages": [
    { "@odata.type": "microsoft.graph.security.mailMessageEntityMapping" }
  ],
  "oAuthApplications": [
    { "@odata.type": "microsoft.graph.security.oAuthApplicationEntityMapping" }
  ],
  "processes": [
    { "@odata.type": "microsoft.graph.security.processEntityMapping" }
  ],
  "registryValues": [
    { "@odata.type": "microsoft.graph.security.registryValueEntityMapping" }
  ],
  "securityGroups": [
    { "@odata.type": "microsoft.graph.security.securityGroupEntityMapping" }
  ],
  "urls": [
    { "@odata.type": "microsoft.graph.security.urlEntityMapping" }
  ]
}
```
