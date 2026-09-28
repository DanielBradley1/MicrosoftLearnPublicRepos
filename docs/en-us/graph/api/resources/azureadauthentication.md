<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureadauthentication?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-10 -->

# azureADAuthentication resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Microsoft Entra Health service level agreement \(SLA\) attainment for each month for a Microsoft Entra tenant. For more information, see [What is Microsoft Entra Health?](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-microsoft-entra-health)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get SLA attainment](https://learn.microsoft.com/en-us/graph/api/azureadauthentication-get?view=graph-rest-beta) | [azureADAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/azureadauthentication?view=graph-rest-beta) | Read the properties and relationships of an [azureADAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/azureadauthentication?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attainments | [serviceLevelAgreementAttainment](https://learn.microsoft.com/en-us/graph/api/resources/servicelevelagreementattainment?view=graph-rest-beta) collection | SLA data for a Microsoft Entra tenant for a calendar month. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureADAuthentication",
  "attainments": [
    {
      "@odata.type": "microsoft.graph.serviceLevelAgreementAttainment"
    }
  ]
}
```
