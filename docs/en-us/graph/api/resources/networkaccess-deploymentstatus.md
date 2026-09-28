<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deploymentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-28 -->

# deploymentStatus resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status of a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) performed through the Global Secure Access services.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deploymentStage | microsoft.graph.networkaccess.deploymentStage | Indicates the current stage of the deployment. The possible values are: `pending`, `inProgress`, `failed`, `succeeded`, `unknownFutureValue`. |
| message | String | Provides additional information or context about the deployment status, such as error details or progress updates. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.deploymentStatus",
  "deploymentStage": "String",
  "message": "String"
}
```
