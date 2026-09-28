<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumeratedscopesensitivitylabels?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# enumeratedScopeSensitivityLabels resource type

Namespace: microsoft.graph.enumeratedScopeSensitivityLabels

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies that only specific sensitivity labels on a resource app in a [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy?view=graph-rest-beta) are preapproved for consent. It can also be used to specify condition sets that are included or excluded in a [permission grant policy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-beta). If the client application requests access to more resource scopes after the policy is created, the policy will still apply.

Inherits from [scopeSensitivityLabels](https://learn.microsoft.com/en-us/graph/api/resources/scopesensitivitylabels?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| labelKind | labelKind | Indicates the kind of sensitivity label that is included. Only `enumerated` is supported to indicate that a selected set of sensitivity labels from a single resource application is allowed. Required. |
| sensitivityLabels | String collection | The sensitivity labels that are applicable to the scope type and have been preapproved. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedScopeSensitivityLabels",
  "labelKind": "String",
  "sensitivityLabels": [
    "String"
  ]
}
```
