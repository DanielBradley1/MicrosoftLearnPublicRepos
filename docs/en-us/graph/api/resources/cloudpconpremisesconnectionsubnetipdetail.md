<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionsubnetipdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# cloudPcOnPremisesConnectionSubnetIpDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the subnet IP details of a [Cloud PC on-premises connection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-beta).

Important

**On-premises network connection** has been renamed as **Azure network connection**. **cloudPcOnPremisesConnection** objects here are equivalent to **Azure network connection** for the Cloud PC product.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| subnetAvailableIpCount | Int32 | The number of available private IP addresses within the subnet. |
| subnetAvailableIpCountLastSyncDateTime | DateTimeOffset | Indicates the date and time at which the subnet available IP count was synced with Azure. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnectionSubnetIpDetail",
  "subnetAvailableIpCount": "Int32",
  "subnetAvailableIpCountLastSyncDateTime": "String (timestamp)"
}
```
