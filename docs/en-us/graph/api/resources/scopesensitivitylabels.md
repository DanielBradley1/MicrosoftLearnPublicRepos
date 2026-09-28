<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/scopesensitivitylabels?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# scopeSensitivityLabels resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines the sensitivity labels for groups that are included in a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta), or included or excluded in a [permission grant policy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-beta). Since **chat** resources don't support sensitivity labels, use `all` when the **scopeType** of [preApprovalDetail](https://learn.microsoft.com/en-us/graph/api/resources/preapprovaldetail?view=graph-rest-beta) is `chat`. For more information about sensitivity labels, see [sensitivity labels](https://learn.microsoft.com/en-us/microsoft-365/compliance/sensitivity-labels).

This resource is an abstract base type from which the following types are derived:

- [allscopesensitivitylabels](https://learn.microsoft.com/en-us/graph/api/resources/allscopesensitivitylabels?view=graph-rest-beta) indicates all sensitivity labels are preapproved
- [enumeratedscopesensitivitylabels](https://learn.microsoft.com/en-us/graph/api/resources/enumeratedscopesensitivitylabels?view=graph-rest-beta) indicates that only the specified sensitivity labels are preapproved

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| labelKind | String | Indicates the kind of sensitivity label that is included. Possible values: `all` means all sensitivity labels are allowed, or `enumerated` means a selected set of sensitivity labels from a single resource application are allowed. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.scopeSensitivityLabels",
  "labelKind": "String"
}
```
