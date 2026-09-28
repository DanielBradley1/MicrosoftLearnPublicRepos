<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-23 -->

# identityCorrelation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an identity correlation report that captures the results of correlating identities between an on-premises directory and Microsoft Entra ID for a specific service principal.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/reportroot-list-correlations?view=graph-rest-beta) | [identityCorrelation](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta) collection | Get a list of the [identityCorrelation](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitycorrelation-get?view=graph-rest-beta) | [identityCorrelation](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta) | Read the properties and relationships of an [identityCorrelation](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta) object. |
| [List identities](https://learn.microsoft.com/en-us/graph/api/identitycorrelation-list-identities?view=graph-rest-beta) | [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) collection | List the correlated identities for this identity correlation report. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | The date and time when the correlation process completed. |
| error | [correlationError](https://learn.microsoft.com/en-us/graph/api/resources/correlationerror?view=graph-rest-beta) | Error information if the correlation process failed. `null` if successful.  <br>  <br>Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the identity correlation report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).  <br>  <br>Supports `$filter` \(`eq`\). |
| startDateTime | DateTimeOffset | The date and time when the correlation process started. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identities | [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) collection | The collection of correlated identity results for this correlation report. |
| servicePrincipal | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta) | The service principal associated with this correlation report. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityCorrelation",
  "id": "String (identifier)",
  "startDateTime": "DateTimeOffset",
  "endDateTime": "DateTimeOffset",
  "error": {
    "@odata.type": "microsoft.graph.correlationError"
  },
  "servicePrincipal": {
    "@odata.type": "microsoft.graph.servicePrincipal"
  }
}
```
