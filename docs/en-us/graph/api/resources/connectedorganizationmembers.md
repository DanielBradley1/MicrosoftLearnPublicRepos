<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/connectedorganizationmembers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# connectedOrganizationMembers resource type

Namespace: microsoft.graph

Used in the **allowedRequestors** property of [accessPackageAssignmentRequestorSettings](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestorsettings?view=graph-rest-1.0) for an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). The `@odata.type` value `#microsoft.graph.connectedOrganizationMembers` indicates that this type identifies a collection of users who are associated with a [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) and are allowed to request an access package.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectedOrganizationId | String | The ID of the [connected organization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) in entitlement management. |
| description | String | The name of the connected organization. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.connectedOrganizationMembers",
  "connectedOrganizationId": "String",
  "description": "String"
}
```
