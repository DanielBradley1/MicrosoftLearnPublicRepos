<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/linkroleabilities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# linkRoleAbilities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the sharing link operations for a link of a specified role.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addExistingExternalUsers | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if the current user can add existing external user recipients to this sharing link. |
| addNewExternalUsers | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if the current user can add new external user recipients to this sharing link. |
| applyVariants | [sharingLinkVariants](https://learn.microsoft.com/en-us/graph/api/resources/sharinglinkvariants?view=graph-rest-beta) | Indicates the status of the potential sharing link variants. If selected, it generates a separate sharing link from the sharing link that would otherwise be generated without the variant, yet with an identical role and scope. |
| createLink | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if links of this role can be created. |
| deleteLink | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if links of this role can be deleted. |
| linkAllowsExternalUsers | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if this link can include external users. |
| linkExpiration | [sharingLinkExpirationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharinglinkexpirationstatus?view=graph-rest-beta) | Indicates if links must expire, meaning the link is no longer usable after a specified time. If link expiration is enabled, a default link expiration time is provided. |
| retrieveLink | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if links of this role can be retrieved. |
| updateLink | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates if links of this role can be updated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.linkRoleAbilities",
  "createLink": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "retrieveLink": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "updateLink": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "deleteLink": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "applyVariants": {
    "@odata.type": "microsoft.graph.sharingLinkVariants"
  },
  "linkExpiration": {
    "@odata.type": "microsoft.graph.sharingLinkExpirationStatus"
  },
  "addNewExternalUsers": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "addExistingExternalUsers": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "linkAllowsExternalUsers": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  }
}
```
