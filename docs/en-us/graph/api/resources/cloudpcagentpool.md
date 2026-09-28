<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpool?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcAgentPool resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an agent pool for Cloud PC provisioning with additional agent-pool-specific configurations.

Inherits from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta).

## Methods

For the list of supported methods, see [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| billingConfiguration | [cloudPcAgentPoolBillingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolbillingconfiguration?view=graph-rest-beta) | The billing configuration for the agent pool. |
| capabilities | [cloudPcPoolCapabilityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolcapabilityconfiguration?view=graph-rest-beta) | The capabilities configuration for the pool, including single sign-on settings. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| cloudPcConfiguration | [cloudPcConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconfiguration?view=graph-rest-beta) | The Cloud PC specification, including image and operating system locale settings. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the pool was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`. Read-only. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| description | String | The description of the pool. The maximum length is 512 characters. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| displayName | String | The display name of the pool. The name is unique across Cloud PC pools in an organization. The maximum length is 60 characters. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| id | String | The unique identifier for the pool. Read-only. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the pool was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026 is `2026-01-01T00:00:00Z`. Read-only. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| networkConfiguration | [cloudPcNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcnetworkconfiguration?view=graph-rest-beta) | The network configuration for the pool. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |
| poolUrl | String | The endpoint URL used to check out and check in agent sessions. This value becomes available after the pool reaches the active status. Read-only. |
| scalingPolicy | [cloudPcAgentPoolScalingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolscalingpolicy?view=graph-rest-beta) | The scaling policy defining minimum and maximum counts. |
| sessionUsage | [cloudPcAgentPoolSessionUsage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolsessionusage?view=graph-rest-beta) | The current session usage of the agent pool. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) collection | The collection of assignments that grant user or service principal identities access to this pool. Inherited from [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAgentPool",
  "billingConfiguration": {
    "@odata.type": "microsoft.graph.cloudPcAgentPoolBillingConfiguration"
  },
  "capabilities": {
    "@odata.type": "microsoft.graph.cloudPcPoolCapabilityConfiguration"
  },
  "cloudPcConfiguration": {
    "@odata.type": "microsoft.graph.cloudPcConfiguration"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "networkConfiguration": {
    "@odata.type": "microsoft.graph.cloudPcNetworkConfiguration"
  },
  "poolUrl": "String",
  "scalingPolicy": {
    "@odata.type": "microsoft.graph.cloudPcAgentPoolScalingPolicy"
  },
  "sessionUsage": {
    "@odata.type": "microsoft.graph.cloudPcAgentPoolSessionUsage"
  }
}
```
