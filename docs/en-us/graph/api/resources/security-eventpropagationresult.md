<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-eventpropagationresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# eventPropagationResult resource type

Namespace: microsoft.graph.security

Represents the status of a retention event creation request and additional information about the scoped locations.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | microsoft.graph.security.eventPropagationStatus | Indicates the status of the event creation request. The possible values are: `none`, `inProcessing`, `failed`, `success`, `unknownFutureValue`. |
| statusInformation | String | Additional information about the status of the event creation request. |
| serviceName | String | The name of the workload associated with the event. |
| location | String | The name of the specific location in the workload associated with the event. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.eventPropagationResult",
  "serviceName": "String",
  "location": "String",
  "status": "String",
  "statusInformation": "String"
}
```
