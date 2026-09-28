<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/correlationerror?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-23 -->

# correlationError resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents error details when a correlation report fails to be created or an individual identity fails to be correlated. Returned in the **error** property of [identityCorrelation](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta) and [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code indicating why the correlation failed. |
| message | String | A human-readable description of the error. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.correlationError",
  "code": "String",
  "message": "String"
}
```
