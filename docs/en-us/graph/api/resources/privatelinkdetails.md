<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privatelinkdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# privateLinkDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides details about the Azure Private Link associated with a sign-in event. This object is configured in the **privateLinkDetails** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta). For more information on Azure Private Link, see [What is Azure Private Link?](https://learn.microsoft.com/en-us/azure/private-link/private-link-overview)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| policyId | String | The unique identifier for the Private Link policy. |
| policyName | String | The name of the Private Link policy in Microsoft Entra ID. |
| policyTenantId | String | The tenant identifier of the Microsoft Entra tenant the Private Link policy belongs to. |
| resourceId | String | The Azure Resource Manager \(ARM\) path for the Private Link policy resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.privateLinkDetails",
  "policyId": "String",
  "policyName": "String",
  "resourceId": "String",
  "policyTenantId": "String"
}
```
