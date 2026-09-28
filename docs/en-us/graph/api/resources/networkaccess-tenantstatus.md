<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tenantstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# tenantStatus resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status of the Global Secure Access services for the tenant.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-tenantstatus-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.tenantStatus](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tenantstatus?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.tenantStatus](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tenantstatus?view=graph-rest-beta) object. |
| [Onboard](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-onboard?view=graph-rest-beta) | [microsoft.graph.networkaccess.tenantStatus](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tenantstatus?view=graph-rest-beta) | Onboard the tenant to the Global Secure Access services. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| onboardingErrorMessage | String | Reflects a message to the user if there's an error. |
| onboardingStatus | microsoft.graph.networkaccess.onboardingStatus | Reflects the tenant onboarding status. The possible values are: `offboarded`, `offboardingInProgress`, `onboardingInProgress`, `onboarded`, `onboardingErrorOccurred`, `offboardingErrorOccurred`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tenantStatus",
  "id": "String (identifier)",
  "onboardingStatus": "String",
  "onboardingErrorMessage": "String"
}
```
