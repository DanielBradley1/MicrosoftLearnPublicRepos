<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/preapprovaldetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# preApprovalDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A preApprovalDetail describes a list of conditions under which the app has been preapproved for consent. The conditions include permissions, resource scope type, and sensitivity labels that have been tagged for the resource scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| permissions | [preApprovedPermissions](https://learn.microsoft.com/en-us/graph/api/resources/preapprovedpermissions?view=graph-rest-beta) | Specifies the permissions being preapproved for consent. Required. |
| scopeType | resourceScopeType | The resource type the preapproval applies to. Possible values: `group` for [groups](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta) and [teams](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta), or `chat` for [chats](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-beta). Required. |
| sensitivityLabels | [scopeSensitivityLabels](https://learn.microsoft.com/en-us/graph/api/resources/scopesensitivitylabels?view=graph-rest-beta) | Conditions on the [sensitivity labels](https://learn.microsoft.com/en-us/microsoftteams/sensitivity-labels) of the target resource scope the preapproval applies to. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.preApprovalDetail",
  "scopeType": "String",
  "sensitivityLabels": {
    "@odata.type": "microsoft.graph.scopeSensitivityLabels"
  },
  "permissions": {
    "@odata.type": "microsoft.graph.preApprovedPermissions"
  }
}
```
