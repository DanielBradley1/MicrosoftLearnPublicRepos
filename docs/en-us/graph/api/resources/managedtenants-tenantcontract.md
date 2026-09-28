<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcontract?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenantContract resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents relationship information between a tenant and the managing entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contractType | Int32 | The type of relationship that exists between the managing entity and tenant. Optional. Read-only. |
| defaultDomainName | String | The default domain name for the tenant. Required. Read-only. |
| displayName | String | The display name for the tenant. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantContract",
  "contractType": "Integer",
  "displayName": "String",
  "defaultDomainName": "String"
}
```
