<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensionresponsedata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# customTaskExtensionResponseData resource type

Namespace: microsoft.graph.identityGovernance

Represents the data returned from [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) callouts. This object is configured in the **data** property of the [customExtensionCalloutResponse](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutresponse?view=graph-rest-1.0) resource.

Inherits from [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operationStatus | microsoft.graph.identityGovernance.customTaskExtensionOperationStatus | The operation status reported by the custom task extension. The possible values are: `completed`, `failed`, `unknownFutureValue`. |
| statusReasons | String collection | A collection of status reason strings. May be empty. |
| targetSubject | [microsoft.graph.identityGovernance.workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0) | The workflow subject that was processed by the custom task extension. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtensionResponseData",
  "operationStatus": "String",
  "targetSubject": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSubject"
  },
  "statusReasons": [
    "String"
  ]
}
```
