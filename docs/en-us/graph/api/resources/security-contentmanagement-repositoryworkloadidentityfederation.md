<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryworkloadidentityfederation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryWorkloadIdentityFederation resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the read-only **workloadIdentityFederation** property of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | Application \(client\) id of the parent application. |
| federatedCredentialId | String | Federated credential id. |
| issuer | String | Federated credential issuer. |
| subject | String | Federated credential subject. |
| tenantId | String | Tenant id that owns the parent application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryWorkloadIdentityFederation",
  "federatedCredentialId": "String",
  "tenantId": "String",
  "appId": "String",
  "subject": "String",
  "issuer": "String"
}
```
