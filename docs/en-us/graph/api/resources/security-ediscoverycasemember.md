<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-13 -->

# ediscoveryCaseMember resource type

Namespace: microsoft.graph.security

Represents an eDiscovery case member. In the context of eDiscovery, case members are granted access to an [ediscoveryCase](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycase?view=graph-rest-1.0) and its data. These cases are accessible to case members via the eDiscovery UX portal or through the eDiscovery case Microsoft Graph APIs. Case members can be one of two types: a user or a role group. For more information, see [Add or remove members from an eDiscovery \(premium\) case](https://learn.microsoft.com/en-us/purview/ediscovery-add-or-remove-members-from-a-case).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasemember-list?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCaseMember](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0) collection | Get a list of the ediscoveryCaseMember objects and their properties. |
| [Add](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasemember-post?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCaseMember](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycasemember?view=graph-rest-1.0) | Add a case member. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycasemember-delete?view=graph-rest-1.0) | None | Remove a case member. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recipientType | microsoft.graph.security.recipientType | Specifies the recipient type of the eDiscovery case member. The possible values are: `user`, `roleGroup`, `unknownFutureValue`. |
| id | String | The ID of the eDiscovery case member. |
| displayName | String | The display name of the eDiscovery case member. Allowed only for case members of type `roleGroup`. |
| smtpAddress | String | The smtp address of the eDiscovery case member. Allowed only for case members of type `user`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryCaseMember",
  "id": "String (identifier)",
  "recipientType": "'@odata.type': 'microsoft.graph.security.recipientType'",
  "displayName": "String",
  "smtpAddress": "String"
}
```
