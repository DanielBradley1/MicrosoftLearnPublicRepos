<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mergeresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# mergeResponse resource type

Namespace: microsoft.graph.security

Represents the response from [move alerts](https://learn.microsoft.com/en-us/graph/api/security-alert-movealerts?view=graph-rest-1.0) or [merge incidents](https://learn.microsoft.com/en-us/graph/api/security-incident-mergeincidents?view=graph-rest-1.0) operations.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| targetIncidentId | String | The ID of the target [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) after the operation completes. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "targetIncidentId": "String"
}
```
