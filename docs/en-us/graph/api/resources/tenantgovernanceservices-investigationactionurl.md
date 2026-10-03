<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionurl?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# investigationActionUrl resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a follow-on API reference for an investigation step returned with [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) metrics. It identifies an existing Microsoft Graph or Azure Resource Manager \(ARM\) API that a client can call to reveal more detail behind an aggregate metric. The **actionUrl** property of the [investigationActionStep](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionstep?view=graph-rest-beta) resource uses this type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | A machine-readable directive that describes how a client should run the step, in the form `metricPath§operation§input§output` \(for example, `b2BRegistrationMetrics.recent.inboundTotalUsers§single§§$verifiedDomains`\). Clients use this value to chain steps together and to interpret the output of the associated **url**. |
| url | String | A Microsoft Graph or Azure Resource Manager \(ARM\) URL template that the client invokes to retrieve the drill-in data for the step. The template can include placeholders such as `{@id}`, `{startDate}`, `{endDate}`, or `{sourceDomain}` that the client resolves from the related tenant, the caller context, or the output of earlier steps. This value can be empty for steps that only transform data returned by a previous step. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.investigationActionUrl",
  "displayName": "String",
  "url": "String"
}
```
