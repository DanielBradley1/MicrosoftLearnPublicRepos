<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryserviceprincipal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryServicePrincipal resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the read-only **servicePrincipal** property of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | Application \(client\) id of the identity. |
| credentialsExpireDateTime | DateTimeOffset | When the identity's credentials expire. |
| servicePrincipalId | String | Object id of the service principal. |
| tenantId | String | Tenant id that owns the identity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryServicePrincipal",
  "servicePrincipalId": "String",
  "tenantId": "String",
  "appId": "String",
  "credentialsExpireDateTime": "String (timestamp)"
}
```
