<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenantInformation resource type

Namespace: microsoft.graph

Information about your Microsoft Entra tenant that is publicly displayed to users in other Microsoft Entra tenants.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Find tenant by domain name](https://learn.microsoft.com/en-us/graph/api/tenantrelationship-findtenantinformationbydomainname?view=graph-rest-1.0) | tenantInformation | Given a domain name, search for a tenant and read its information. |
| [Find tenant by tenant ID](https://learn.microsoft.com/en-us/graph/api/tenantrelationship-findtenantinformationbytenantid?view=graph-rest-1.0) | tenantInformation | Given a tenant ID, search for a tenant and read its information. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultDomainName | String | Primary domain name of a Microsoft Entra tenant. |
| displayName | String | Display name of a Microsoft Entra tenant. |
| federationBrandName | String | Name shown to users that sign in to a Microsoft Entra tenant. |
| tenantId | String | Unique identifier of a Microsoft Entra tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantInformation",
  "defaultDomainName": "String",
  "displayName": "String",
  "federationBrandName": "String",
  "tenantId": "String"
}
```
