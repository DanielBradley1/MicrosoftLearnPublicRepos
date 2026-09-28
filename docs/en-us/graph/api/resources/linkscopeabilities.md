<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/linkscopeabilities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# linkScopeAbilities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the sharing abilities for each possible sharingRole within a particular sharing link scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockDownloadLinkAbilities | [linkRoleAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta) | The blockDownload link abilities. |
| editLinkAbilities | [linkRoleAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta) | The edit link abilities. |
| manageListLinkAbilities | [linkRoleAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta) | The manageList link abilities. |
| readLinkAbilities | [linkRoleAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta) | The read link abilities. |
| reviewLinkAbilities | [linkRoleAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta) | The review link abilities. |
| submitOnlyLinkAbilities | [linkRoleAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta) | The submitOnly link abilities. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.linkScopeAbilities",
  "readLinkAbilities": {
    "@odata.type": "microsoft.graph.linkRoleAbilities"
  },
  "editLinkAbilities": {
    "@odata.type": "microsoft.graph.linkRoleAbilities"
  },
  "reviewLinkAbilities": {
    "@odata.type": "microsoft.graph.linkRoleAbilities"
  },
  "manageListLinkAbilities": {
    "@odata.type": "microsoft.graph.linkRoleAbilities"
  },
  "blockDownloadLinkAbilities": {
    "@odata.type": "microsoft.graph.linkRoleAbilities"
  },
  "submitOnlyLinkAbilities": {
    "@odata.type": "microsoft.graph.linkRoleAbilities"
  }
}
```
