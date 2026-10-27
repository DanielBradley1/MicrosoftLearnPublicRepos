<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/evaluationscope?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# evaluationScope resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the scope used for data protection policy evaluation.

Set in the **evaluationScope** property of [processContentRequest](https://learn.microsoft.com/en-us/graph/api/resources/processcontentrequest?view=graph-rest-beta) or the **evaluationScope** parameter of [tenantProtectionScopeContainer: compute](https://learn.microsoft.com/en-us/graph/api/tenantprotectionscopecontainer-compute?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | [evaluationScopeType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#evaluationscopetype-values) | The evaluation scope. Possible values are `tenant`, `agent`, `anonymousUser`, and `unknownFutureValue`. Required. Use `agent` to evaluate data loss prevention policies for agent interactions. |

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
