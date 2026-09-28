<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# customExtensionCalloutInstance resource type

Namespace: microsoft.graph

Defines the calls that were made by an instance of a custom extension callout.

In entitlement management, this object is configured in the **customExtensionCalloutInstances** property of [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) and [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customExtensionId | String | Identification of the custom extension that was triggered at this instance. |
| detail | String | Details provided by the logic app during the callback of the request instance. |
| externalCorrelationId | String | The unique run identifier for the logic app. |
| id | String | Unique identifier for the callout instance. Read-only. |
| status | customExtensionCalloutInstanceStatus | The status of the request to the custom extension. The possible values are: `calloutSent`, `callbackReceived`, `calloutFailed`, `callbackTimedOut`, `waitingForCallback`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionCalloutInstance",
  "id": "String (identifier)",
  "customExtensionId": "String",
  "externalCorrelationId": "String",
  "detail": "String",
  "status": "String"
}
```
