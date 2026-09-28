<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcontactinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# tenantContactInformation resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a contact at a managed tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| email | String | The email address for the contact. Optional |
| name | String | The name for the contact. Required. |
| notes | String | The notes associated with the contact. Optional |
| phone | String | The phone number for the contact. Optional. |
| title | String | The title for the contact. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantContactInformation",
  "name": "String",
  "title": "String",
  "email": "String",
  "phone": "String",
  "notes": "String"
}
```
