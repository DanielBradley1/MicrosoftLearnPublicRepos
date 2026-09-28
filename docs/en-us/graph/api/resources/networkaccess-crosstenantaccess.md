<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-crosstenantaccess?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# crossTenantAccess resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains usage count and external tenant information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceCount | Int64 | The number of devices that accessed the external tenant. |
| lastAccessDateTime | DateTimeOffset | The timestamp of the most recent access to the external tenant. |
| resourceTenantId | String | The tenant ID of the external tenant. |
| resourceTenantName | String | The name of the external tenant. |
| resourceTenantPrimaryDomain | String | The domain of the external tenant. |
| usageStatus | microsoft.graph.networkaccess.usageStatus | The usage status of cross-tenant access. The possible values are `frequentlyUsed`, `rarelyUsed`, and `unknownFutureValue`. |
| userCount | Int64 | The number of users that accessed the external tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.crossTenantAccess",
  "resourceTenantName": "String",
  "usageStatus": "String",
  "resourceTenantId": "String",
  "resourceTenantPrimaryDomain": "String",
  "userCount": "Integer",
  "deviceCount": "Integer",
  "lastAccessDateTime": "String (timestamp)"
}
```
