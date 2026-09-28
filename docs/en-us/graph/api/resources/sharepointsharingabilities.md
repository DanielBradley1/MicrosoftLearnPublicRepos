<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointsharingabilities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# sharePointSharingAbilities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides information about which sharing links are available to the user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| anyoneLinkAbilities | [linkScopeAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkscopeabilities?view=graph-rest-beta) | The anyone link abilities. |
| directSharingAbilities | [directSharingAbilities](https://learn.microsoft.com/en-us/graph/api/resources/directsharingabilities?view=graph-rest-beta) | The direct sharing abilities. |
| organizationLinkAbilities | [linkScopeAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkscopeabilities?view=graph-rest-beta) | The organization link abilities. |
| specificPeopleLinkAbilities | [linkScopeAbilities](https://learn.microsoft.com/en-us/graph/api/resources/linkscopeabilities?view=graph-rest-beta) | The specificPeople link abilities. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointSharingAbilities",
  "anyoneLinkAbilities": {
    "@odata.type": "microsoft.graph.linkScopeAbilities"
  },
  "organizationLinkAbilities": {
    "@odata.type": "microsoft.graph.linkScopeAbilities"
  },
  "specificPeopleLinkAbilities": {
    "@odata.type": "microsoft.graph.linkScopeAbilities"
  },
  "directSharingAbilities": {
    "@odata.type": "microsoft.graph.directSharingAbilities"
  }
}
```
