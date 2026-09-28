<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# deployment resource type \(for networkAccess\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a deployment event within the Global Secure Access services, including its configuration, status, and related data.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-deployments-list?view=graph-rest-beta) | [microsoft.graph.networkaccess.deployment](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) collection | Retrieve a list of logs that include the status of deployments performed through the Global Secure Access services. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-deployments-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.deployment](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) | Retrieve a specific deployment by filtering the list endpoint with the deployment ID. Individual deployment retrieval is performed by applying a filter to the list deployments API. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [microsoft.graph.networkaccess.deploymentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deploymentconfiguration?view=graph-rest-beta) | Specifies the configuration details associated with the deployment, such as the type of configuration change being applied. |
| deploymentEndDateTime | DateTimeOffset | Indicates the date and time when the deployment was completed. |
| initiatedBy | String | Identifies the user or system that initiated the deployment. |
| lastModifiedDateTime | DateTimeOffset | Specifies the date and time when the deployment was last modified. |
| requestId | String | A unique identifier for the deployment request. Primary key. |
| status | [microsoft.graph.networkaccess.deploymentStatus](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deploymentstatus?view=graph-rest-beta) | Represents the current status of the deployment, including its stage and any related messages. Supports `$filter` \(`eq`\) for **status/deploymentState**. For example, `status/deploymentStage eq 'succeeded'`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.deployment",
  "requestId": "String (identifier)",
  "status": {
    "@odata.type": "microsoft.graph.networkaccess.deploymentStatus"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "initiatedBy": "String",
  "deploymentEndDateTime": "String (timestamp)",
  "configuration": {
    "@odata.type": "microsoft.graph.networkaccess.deploymentConfiguration"
  }
}
```
