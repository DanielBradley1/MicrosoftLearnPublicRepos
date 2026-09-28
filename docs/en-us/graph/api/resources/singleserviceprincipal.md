<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/singleserviceprincipal?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-04 -->

# singleServicePrincipal resource type

Namespace: microsoft.graph

Used in the request, approval, and assignment review settings of an access package assignment policy. The `@odata.type` value `#microsoft.graph.singleServicePrincipal` indicates that this [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) identifies a specific service principal in the tenant who will be allowed as a requestor, approver, or reviewer.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of this service principal. |
| servicePrincipalId | String | ID of the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.singleServicePrincipal",
  "servicePrincipalId": "String",
  "description": "String"
}
```
