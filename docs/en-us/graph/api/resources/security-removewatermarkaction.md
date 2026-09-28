<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-removewatermarkaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# removeWatermarkAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action that specifies the details on the content watermark to be removed from the information, if applicable. The [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta), [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta), or [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateremoval?view=graph-rest-beta) APIs might return the **removeWatermarkAction** if the watermark is to be removed as a result of updating or removing the label. The action instructs the consuming application to remove the specific UI element that contains the previously-applicable content watermark.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| uiElementNames | String collection | The name of the UI element of watermark to be removed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.removeWatermarkAction",
  "uiElementNames": [
    "String"
  ]
}
```
