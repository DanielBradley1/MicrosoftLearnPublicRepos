<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-deploymentscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# deploymentScope resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the Azure deployment stack scope in the **deploymentScope** property or **deploymentScope** connect action parameter of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ARM resource id of the scope: a resource group \(/subscriptions/{id}/resourceGroups/{name}\) or a management group \(/providers/Microsoft.Management/managementGroups/{id}\). |
| scopeType | [microsoft.graph.security.contentManagement.deploymentScopeType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#deploymentscopetype-values) | Kind of Azure scope the deployment stack is provisioned at. The possible values are: `resourceGroup`, `managementGroup`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.deploymentScope",
  "scopeType": "String",
  "id": "String"
}
```
