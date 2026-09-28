<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsupportedregion?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# cloudPcSupportedRegion resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a supported region to establish an Azure network connection for Cloud PCs.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-supportedregions?view=graph-rest-beta) | [cloudPcSupportedRegion](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsupportedregion?view=graph-rest-beta) collection | List the supported regions that are available for creating Cloud PC connections. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name for the supported region. Read-only. |
| geographicLocationType | [cloudPcGeographicLocationType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcgeographiclocationtype?view=graph-rest-beta) | The geographic location where the region is located. Read-only. |
| id | String | The unique identifier for the supported region. Read-only. |
| regionGroup | [cloudPcRegionGroup](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcregiongroup?view=graph-rest-beta) | The geographic group this region belongs to. Multiple regions can belong to one region group. For example, the `europeUnion` region group contains the Northern Europe and Western Europe regions. A customer can select a region group when provisioning a Cloud PC; however, the Cloud PC is put under one of the regions under the group based on resource capacity. The region with more quota is chosen. Read-only. |
| regionRestrictionDetail | [cloudPcSupportedRegionRestrictionDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsupportedregionrestrictiondetail?view=graph-rest-beta) | When the region isn't available, all region restrictions are set to `true`. These restrictions apply to four properties: **cPURestricted**, **gPURestricted**, **nestedVirtualizationRestricted** and **availabilityZoneRestricted**. **cPURestricted** indicates whether the region is available for CPU, **gPURestricted** indicates whether the region is available for GPU, **nestedVirtualizationRestricted** indicates whether the region is available for nested virtualization, and **availabilityZoneRestricted** indicates whether the region is available for availability zone support. Read-only. |
| regionStatus | [cloudPcSupportedRegionStatus](#cloudpcsupportedregionstatus-values) | The status of the supported region. The possible values are: `available`, `restricted`, `unavailable`, `unknownFutureValue`. Read-only. |
| supportedSolution | [cloudPcManagementService](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-beta#cloudpcmanagementservice-values) | The supported service or solution for the region. The possible values are: `windows365`, `devBox`, `unknownFutureValue`, `rpaBox`, `microsoft365Opal`, `microsoft365BizChat`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `rpaBox`. Read-only. |

### cloudPcSupportedRegionStatus values

| Member | Description |
| :--- | :--- |
| available | The region is available and fully supports Cloud PCs to be provisioned in that region. |
| restricted | The region is considered a restricted region and can only have a Cloud PC provisioned in that region for specific tenants. |
| unavailable | The region has no support for Cloud PC provisioning. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcSupportedRegion",
  "displayName": "String",
  "id": "String (identifier)",
  "regionGroup": "String",
  "regionRestrictionDetail": {"@odata.type": "microsoft.graph.cloudPcSupportedRegionRestrictionDetail"},
  "regionStatus": "String",
  "geographicLocationType": "String",
  "supportedSolution": "String"
}
```
