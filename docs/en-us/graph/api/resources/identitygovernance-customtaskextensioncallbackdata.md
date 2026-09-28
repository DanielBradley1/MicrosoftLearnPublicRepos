<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# customTaskExtensionCallbackData resource type

Namespace: microsoft.graph.identityGovernance

Represents the operation status that the logic app returns as part of a [customExtensionCalloutResponse](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutresponse?view=graph-rest-1.0). This object is configured in the **data** property of that resource for callbacks from the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) resource.

Inherits from [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operationStatus | microsoft.graph.identityGovernance.customTaskExtensionOperationStatus | Operation status that's provided by the Azure Logic App indicating whenever the Azure Logic App has run successfully or not. Supported values: `completed`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtensionCallbackData",
  "operationStatus": "String"
}
```
