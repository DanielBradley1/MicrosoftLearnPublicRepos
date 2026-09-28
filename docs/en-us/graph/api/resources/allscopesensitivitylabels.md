<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/allscopesensitivitylabels?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# allScopeSensitivityLabels resource type

Namespace: microsoft.graph.allScopeSensitivityLabels

Specifies that sensitivity labels from any resource app in a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) are preapproved for consent. It can also be used to specify condition sets that are included or excluded in a [permission grant policy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-beta). If the client application requests access to more resource scopes after the policy is created, the policy will still apply.

Inherits from [scopeSensitivityLabels](https://learn.microsoft.com/en-us/graph/api/resources/scopesensitivitylabels?view=graph-rest-beta).

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| labelKind | labelKind | Inherited from [scopeSensitivityLabels](https://learn.microsoft.com/en-us/graph/api/resources/scopesensitivitylabels?view=graph-rest-beta). Indicates the scope of sensitivity labels that are included in this condition set. Possible values: `all` for all sensitivity labels, or `enumerated` for a given list of sensitivity labels. Only `all` is supported for the **allScopeSensitivityLabels** object type. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allScopeSensitivityLabels",
  "labelKind": "String"
}
```
