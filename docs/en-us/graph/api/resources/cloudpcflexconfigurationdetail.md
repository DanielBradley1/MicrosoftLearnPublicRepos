<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcflexconfigurationdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# cloudPcFlexConfigurationDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents Windows 365 Flex-specific \(formerly Windows 365 Frontline\) configuration details for a [Cloud PC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta), including license availability. The [retrieveFlexCloudPcConfigurationDetail](https://learn.microsoft.com/en-us/graph/api/cloudpc-retrieveflexcloudpcconfigurationdetail?view=graph-rest-beta) function on the [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta) resource returns this type.

License availability is determined by the service plan and concurrent-access group of the Cloud PC. It doesn't describe the power state of the Cloud PC.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| flexCloudPcAvailability | [cloudPcFlexAvailabilityStatus](#cloudpcflexavailabilitystatus-values) | Whether a Flex license is currently available in the service plan and concurrent-access group of the Cloud PC. The possible values are: `notApplicable`, `available`, `notAvailable`, `unknownFutureValue`. Read-only. |

### cloudPcFlexAvailabilityStatus values

| Member | Description |
| :--- | :--- |
| notApplicable | Flex license availability doesn't apply to this Cloud PC. |
| available | A Flex license is currently available in the service plan and concurrent-access group of the Cloud PC. |
| notAvailable | No Flex license is currently available in the service plan and concurrent-access group of the Cloud PC. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcFlexConfigurationDetail",
  "flexCloudPcAvailability": "String"
}
```
