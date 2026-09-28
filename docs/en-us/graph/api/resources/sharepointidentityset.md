<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentityset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# sharePointIdentitySet resource type

Namespace: microsoft.graph

Represents a keyed collection of [sharePointIdentity](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentity?view=graph-rest-1.0) and [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) resources. This resource extends from the **identitySet** resource to provide the ability to expose SharePoint-specific information to the user.

This resource is used to represent a set of identities associated with various events for an item, such as *created by* or *last modified by*.

For usage information, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The application associated with this action. Optional. |
| device | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The device associated with this action. Optional. |
| group | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The group associated with this action. Optional. |
| sharePointGroup | [sharePointGroupIdentity](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentity?view=graph-rest-1.0) | The SharePoint group associated with this action, identified by a globally unique ID. Use this property instead of **siteGroup** when available. Optional. |
| siteGroup | [sharePointIdentity](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentity?view=graph-rest-1.0) | The SharePoint group associated with this action, identified by a principal ID that is unique only within the site. Optional. |
| siteUser | [sharePointIdentity](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentity?view=graph-rest-1.0) | The SharePoint user associated with this action. Optional. |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The user associated with this action. Optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  /** inherited from IdentitySet **/
  "application": {"@odata.type": "microsoft.graph.identity"},
  "device": {"@odata.type": "microsoft.graph.identity"},
  "user": {"@odata.type": "microsoft.graph.identity"},
  
  "group": {"@odata.type": "microsoft.graph.identity"},
  "siteUser": {"@odata.type": "microsoft.graph.sharePointIdentity"},
  "siteGroup":{"@odata.type": "microsoft.graph.sharePointIdentity"},
  "sharePointGroup": {"@odata.type": "microsoft.graph.sharePointGroupIdentity"}
}
```
