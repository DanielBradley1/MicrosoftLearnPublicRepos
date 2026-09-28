<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/datacollectioninfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# dataCollectionInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the details and status of the data collection process for the authorization system onboarded to Microsoft Entra Permissions Management.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| entitlements | [entitlementsDataCollectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/entitlementsdatacollectioninfo?view=graph-rest-beta) | Represents the details and status of data collection about permissions assigned to an identity in the authorization system. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.dataCollectionInfo",
  "entitlements": {
    "@odata.type": "microsoft.graph.entitlementsDataCollectionInfo"
  }
}
```
