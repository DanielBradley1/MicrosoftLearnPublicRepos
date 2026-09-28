<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementRingAssignmentResult resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the status of an individual assignment within a deployment ring.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| payloadId | Guid | The payload identifier for this assignment. |
| status | [deviceAndAppManagementDeploymentRingAssignmentStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentringassignmentstatus?view=graph-rest-beta) | The status of this assignment. Possible values are: `notActivated`, `activating`, `canceled`, `paused`, `activated`, `error`, `unknownFutureValue`. |
| message | String | Optional status message for this assignment. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementRingAssignmentResult",
  "payloadId": "Guid",
  "status": "String",
  "message": "String"
}
```
