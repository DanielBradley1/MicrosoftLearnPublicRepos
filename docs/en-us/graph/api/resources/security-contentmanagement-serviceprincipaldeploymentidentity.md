<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-serviceprincipaldeploymentidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# servicePrincipalDeploymentIdentity resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies a customer-provided service principal in the **deploymentIdentity** property or connect action parameter of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

Inherits from [microsoft.graph.security.contentManagement.deploymentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-deploymentidentity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationId | String | Application \(client\) id of the customer-supplied service principal. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.servicePrincipalDeploymentIdentity",
  "applicationId": "String"
}
```
