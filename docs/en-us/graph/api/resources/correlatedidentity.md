<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-23 -->

# correlatedIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a correlated identity result, containing the source and target identity details and the correlation status.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitycorrelation-list-identities?view=graph-rest-beta) | [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) collection | Get a list of the [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/correlatedidentity-get?view=graph-rest-beta) | [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) | Read the properties of a [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlatedDateTime | DateTimeOffset | The date and time when the identity was correlated.  <br>  <br>Supports `$orderby`. |
| error | [correlationError](https://learn.microsoft.com/en-us/graph/api/resources/correlationerror?view=graph-rest-beta) | Error information if the correlation for this identity failed. `null` if successful.  <br>  <br>Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the correlated identity. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`\). |
| sourceIdentity | [identityInfo](https://learn.microsoft.com/en-us/graph/api/resources/identityinfo?view=graph-rest-beta) | The source identity information from the on-premises directory.  <br>  <br>Supports `$filter` \(`eq`\). |
| status | String | The correlation and assignment status. Possible values include: `uncorrelated`, `correlatedNotAssigned`, `correlatedAssigned` and `failToCorrelate`.  <br>  <br>Supports `$filter` \(`eq`\), `$count`. |
| targetIdentity | [identityInfo](https://learn.microsoft.com/en-us/graph/api/resources/identityinfo?view=graph-rest-beta) | The target identity information from Microsoft Entra ID.  <br>  <br>Supports `$filter` \(`eq`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.correlatedIdentity",
  "id": "String (identifier)",
  "correlatedDateTime": "DateTimeOffset",
  "sourceIdentity": {
    "@odata.type": "microsoft.graph.identityInfo"
  },
  "targetIdentity": {
    "@odata.type": "microsoft.graph.identityInfo"
  },
  "status": "String",
  "error": {
    "@odata.type": "microsoft.graph.correlationError"
  }
}
```
