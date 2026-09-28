<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicylink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-04 -->

# tlsInspectionPolicyLink resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the link between a [filtering profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) and a [TLS inspection policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta).

Inherits from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta).

## Methods

For supported API operations, see [filteringPolicyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicylink?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the policy link. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | microsoft.graph.networkaccess.status | The state of the policy link. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). The possible values are: `enabled`, `disabled`, `unknownFutureValue`. Supports `$filter` \(`eq`, `ne`\). |
| version | String | Version number of the policy link. Inherited from [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| policy | [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) | The TLS inspection policy associated with this link. The policy is of derived type [microsoft.graph.networkaccess.tlsInspectionpolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicyLink",
  "id": "String (identifier)",
  "state": "String",
  "version": "String"
}
```
