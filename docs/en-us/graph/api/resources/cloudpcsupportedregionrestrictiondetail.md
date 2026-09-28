<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsupportedregionrestrictiondetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# cloudPcSupportedRegionRestrictionDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the restriction status of a [cloudPcSupportedRegion](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsupportedregion?view=graph-rest-beta), including the CPU provisioning status, GPU provisioning status, and nested virtualization provisioning status.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cPURestricted | Boolean | Indicates that the region is restricted for Cloud PC CPU provisioning. `True` indicates that Cloud PC provisioning with CPU isn't available in this region. `false` indicates that it's available. The default value is `false`. Read-only. |
| gPURestricted | Boolean | Indicates that the region is restricted for Cloud PC GPU provisioning. `True` indicates that Cloud PC provisioning with GPU isn't available in this region. `false` indicates that it's available. The default value is `false`. Read-only. |
| nestedVirtualizationRestricted | Boolean | Indicates that the region is restricted for Cloud PC nested virtualization provisioning. `True` indicates that Cloud PC provisioning with nested virtualization isn't available in this region; `false` indicates that it's available. The default value is `false`. Read-only. |
| availabilityZoneRestricted | Boolean | Indicates that the region is restricted due to lack of availability zone support. When `True`, the region does not have availability zone infrastructure and is intended for disaster recovery scenarios only. When `false`, the region has full availability zone support. The default is `false`. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcSupportedRegionRestrictionDetail",
  "cPURestricted": "Boolean",
  "gPURestricted": "Boolean",
  "nestedVirtualizationRestricted": "Boolean",
  "availabilityZoneRestricted": "Boolean"
}
```
