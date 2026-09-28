<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entitlementsdatacollection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# entitlementsDataCollection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the details and status of data collection about permissions assigned to an identity in the authorization system. The API returns this object when it collects data from the authorization system.

Inherits from [entitlementsDataCollectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/entitlementsdatacollectioninfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| lastCollectionDateTime | DateTimeOffset | Last transformation time of entitlements. |
| permissionsModificationCapability | permissionsModificationCapability | Defines whether permissions can be modified in the authorization system. The possible values are: `enabled`, `notConfigured`, `noRecentDataCollected`, `unknownFutureValue`. |
| status | dataCollectionStatus | The entitlements status. The possible values are: `online`, `offline`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.entitlementsDataCollection",
  "status": "String",
  "lastCollectionDateTime": "String (timestamp)",
  "permissionsModificationCapability": "String"
}
```
