<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deploymentconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# deploymentConfiguration resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration details for a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) performed through the Global Secure Access services.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeType | String | Specifies the type of configuration change being deployed. The possible values are: `remoteNetwork`, `enrichedAuditLogsSetting`, `crossTenantAccessSettings`, `conditionalAccessSettings`, `forwardingOptions`, `forwardingProfile`, `filteringProfile`, `unknownFutureValue`. |
| operationName | String | Indicates the name of the operation being performed as part of the deployment configuration. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.deploymentConfiguration",
  "operationName": "String",
  "changeType": "String"
}
```
