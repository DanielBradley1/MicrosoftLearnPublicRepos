<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/frontlinecloudpcdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# frontlineCloudPcDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents current details, such as the availability of a frontline-assigned Cloud PC.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| frontlineCloudPcAvailability | [frontlineCloudPcAvailability](https://learn.microsoft.com/en-us/graph/api/resources/frontlinecloudpcdetail?view=graph-rest-beta#frontlinecloudpcavailability-values) | The current availability of a frontline assigned Cloud PC. The possible values are: `notApplicable`, `available`, `notAvailable`, `unknownFutureValue`. The default value is `notApplicable`. Read-only. |

### frontlineCloudPcAvailability values

| Member | Description |
| :--- | :--- |
| notApplicable | Default. The Cloud PC isn't a frontline-assigned type. |
| available | The current frontline Cloud PC is available and the user is able to connect to it. |
| notAvailable | The frontline Cloud PC is currently not available and the associated user isn't able to connect to it. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.frontlineCloudPcDetail",
  "frontlineCloudPcAvailability": "String"
}
```
