<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionstep?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# investigationActionStep resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an ordered investigation step returned with [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) metrics to help callers drill into the signals behind an aggregate metric. Each step reuses the Microsoft Graph recommendations pattern: it pairs human-readable guidance with an existing Microsoft Graph or Azure Resource Manager \(ARM\) API that, when called, reveals more information about the quality, quantity, or source of the connections behind the aggregate metric. Investigation steps are computed at read time and returned through the **investigationHints** relationship on metrics resources such as [b2bRegistrationMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetrics?view=graph-rest-beta), [b2BSignInActivityMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-beta), [multiTenantApplicationMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetrics?view=graph-rest-beta), and [billingMetrics](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetrics?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionUrl | [microsoft.graph.investigationActionUrl](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionurl?view=graph-rest-beta) | The follow-on API reference for the step, containing the URL template and a machine-readable execution directive that a client uses to retrieve the drill-in data. |
| stepNumber | String | The one-based order, as a string, in which the step should be evaluated by a client. Steps are intended to be run in ascending **stepNumber** order because later steps can depend on the output of earlier steps. This value is the key of the resource. |
| text | String | Human-readable guidance that explains what the step does and why it's useful for investigating the related metric. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.investigationActionStep",
  "stepNumber": "String (identifier)",
  "text": "String",
  "actionUrl": {
    "@odata.type": "microsoft.graph.investigationActionUrl"
  }
}
```
