<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-associatedbranch?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# associatedBranch resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A branch office location associated with a traffic profile.

Inherits from [microsoft.graph.networkaccess.association](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-association?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| branchId | String | Identifier for the branch. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.associatedBranch",
  "branchId": "String"
}
```
