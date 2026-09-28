<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitempolicydetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdateCatalogItemPolicyDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Class to describe quality update policy's approval detail for specific catalog item

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| policyId | Guid | Policy Id for this approval intend |
| catalogItemId | String | Catalog item id for this approval intend |
| approvalStatus | [windowsQualityUpdateApprovalStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateapprovalstatus?view=graph-rest-beta) | Approval status for this approval intend. Possible values are: `unknown`, `approved`, `suspended`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateCatalogItemPolicyDetail",
  "policyId": "Guid",
  "catalogItemId": "String",
  "approvalStatus": "String"
}
```
