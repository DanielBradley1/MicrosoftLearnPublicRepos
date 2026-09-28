<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/evaluationscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# evaluationScope resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the evaluation context used when Microsoft Purview evaluates content or computes protection scopes.

The evaluation scope determines how policies are resolved for a request. By default, requests are evaluated using the tenant context. For Agent-to-Tool \(A2T\) scenarios, set the **type** property to `agent` to enable agent-aware policy evaluation, which considers both agent and tool locations when resolving applicable Microsoft Purview Data Loss Prevention \(DLP\) policies.

This resource is used by the following APIs:

- `protectionScopes/compute`
- `processContent`

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | evaluationScopeType | Specifies the evaluation context for the request. Required. Set to `agent` for Agent-to-Tool \(A2T\) scenarios to enable policy evaluation based on `policyLocationApplication` and `policyLocationTool`. The possible values are: `tenant`, `agent`, `anonymousUser`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.evaluationScope",
  "type": "String"
}
```
