<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsmanagement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsManagement resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

The base container for the relationships that define the requests for permissions in an authorization system onboarded to Microsoft Entra Permissions Management.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| permissionsRequestChanges | [permissionsRequestChange](https://learn.microsoft.com/en-us/graph/api/resources/permissionsrequestchange?view=graph-rest-beta) | Represents a change event of the scheduledPermissionsRequest entity. |
| scheduledPermissionsRequests | [scheduledPermissionsRequest](https://learn.microsoft.com/en-us/graph/api/resources/scheduledpermissionsrequest?view=graph-rest-beta) | Represents a permissions request that Permissions Management uses to manage permissions for an identity on resources in the authorization system. This request can be granted, rejected or canceled by identities in Permissions Management. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsManagement"
}
```
