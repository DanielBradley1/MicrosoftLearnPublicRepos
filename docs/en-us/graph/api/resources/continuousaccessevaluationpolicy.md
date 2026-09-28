<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# continuousAccessEvaluationPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Continuous Access Evaluation \(CAE\) manages authentication sessions in real time. CAE allows customers to handle access to resources by supporting instant revocation events. For more information, see the [Continuous access evaluation](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-continuous-access-evaluation).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/continuousaccessevaluationpolicy-get?view=graph-rest-beta) | [continuousAccessEvaluationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationpolicy?view=graph-rest-beta) | Read the properties of a [continuousAccessEvaluationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationpolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/continuousaccessevaluationpolicy-update?view=graph-rest-beta) | [continuousAccessEvaluationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationpolicy?view=graph-rest-beta) | Update the properties of a [continuousAccessEvaluationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationpolicy?view=graph-rest-beta) object. |
|  |  |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Continuous access evaluation automatically blocks access to resources and applications in near real time when a user's access is removed or a client IP address changes. Read-only. |
| displayName | String | The value is always `Continuous Access Evaluation`. Read-only. |
| groups | String collection | The collection of group identifiers in scope for evaluation. All groups are in scope when the collection is empty. Read-only. |
| id | String | Specifies the identifier of a [continuousAccessEvaluationPolicy](#continuousaccessevaluationpolicy-resource-type) object. Read-only. |
| isEnabled | Boolean | `true` to indicate whether continuous access evaluation should be performed; otherwise `false`. Read-only. |
| users | String collection | The collection of user identifiers in scope for evaluation. All users are in scope when the collection is empty. Read-only. |
| migrate | Boolean | `true` to indicate that the continuous access evaluation policy settings should be or has been migrated to the conditional access policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.continuousAccessEvaluationPolicy",
  "id": "String (identifier)",
  "description": "String",
  "displayName": "String",
  "isEnabled": "Boolean",
  "users": [
    "String"
  ],
  "groups": [
    "String"
  ],
  "migrate": "Boolean"
}
```
