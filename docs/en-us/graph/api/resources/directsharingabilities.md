<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directsharingabilities?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# directSharingAbilities resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the direct sharing abilities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addExistingExternalUsers | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether the current user can add existing guest recipients to this item using direct sharing. |
| addInternalUsers | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether the current user can add internal recipients to this item using direct sharing. |
| addNewExternalUsers | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether the current user can add new guest recipients to this item using direct sharing. |
| requestGrantAccess | [sharingOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta) | Indicates whether the user querying this endpoint can request access for the user or on behalf of other users, after which, site admins, can approve or deny the creation of a potential sharing link. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.directSharingAbilities",
  "requestGrantAccess": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "addNewExternalUsers": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "addExistingExternalUsers": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  },
  "addInternalUsers": {
    "@odata.type": "microsoft.graph.sharingOperationStatus"
  }
}
```
