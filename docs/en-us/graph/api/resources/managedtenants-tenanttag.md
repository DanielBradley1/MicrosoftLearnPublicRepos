<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# tenantTag resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a tag that can be assigned to managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tenant tags](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-tenanttags?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) collection | Get a list of the [tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) objects and their properties. |
| [Create tenant tag](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-post-tenanttags?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) | Create a new [tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) object. |
| [Get tenant tag](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenanttag-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) | Read the properties and relationships of a [tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) object. |
| [Update tenant tag](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenanttag-update?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) | Update the properties of a [tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) object. |
| [Delete tenant tag](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenanttag-delete?view=graph-rest-beta) | None | Deletes a [tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) object. |
| [Assign tenant tag](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenanttag-assigntag?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) | Assigns the tenant tag to the specified managed tenants. |
| [Unassign tenant tag](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenanttag-unassigntag?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantTag](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenanttag?view=graph-rest-beta) | Un-assigns the tenant tag from the specified managed tenants. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdByUserId | String | The identifier for the account that created the tenant tag. Required. Read-only. |
| createdDateTime | DateTimeOffset | The date and time when the tenant tag was created. Required. Read-only. |
| deletedDateTime | DateTimeOffset | The date and time when the tenant tag was deleted. Required. Read-only. |
| description | String | The description for the tenant tag. Optional. Read-only. |
| displayName | String | The display name for the tenant tag. Required. Read-only. |
| id | String | The unique identifier for the tenant tag. Required. Read-only. |
| lastActionByUserId | String | The identifier for the account that lasted on the tenant tag. Optional. Read-only. |
| lastActionDateTime | DateTimeOffset | The date and time the last action was performed against the tenant tag. Optional. Read-only. |
| tenants | [microsoft.graph.managedTenants.tenantInfo](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantinfo?view=graph-rest-beta) collection | The collection of managed tenants associated with the tenant tag. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.tenantTag",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdByUserId": "String",
  "lastActionByUserId": "String",
  "tenants": [
    {
      "@odata.type": "microsoft.graph.managedTenants.tenantInfo"
    }
  ],
  "lastActionDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "deletedDateTime": "String (timestamp)"
}
```
